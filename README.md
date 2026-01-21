# NetPerf-RCA Benchmark

## Resumo
Este repositório contém o NetPerf-RCA Benchmark, um conjunto de 24 cenários de falhas em redes e sistemas virtualizados destinado à avaliação de técnicas de diagnóstico automatizado, especialmente com modelos de linguagem.

## Estrutura
- data/prompts.jsonl: prompts enviados aos modelos
- data/scenarios.jsonl: diagnósticos esperados (ground truth)
- scripts/: scripts de avaliação

## Convenções de Nomenclatura e Níveis de Abstração

O NetPerf-RCA Benchmark adota intencionalmente diferentes níveis de abstração para descrever cada cenário de falha, com o objetivo de separar a caracterização do problema da sua causa raiz específica.

- O campo `scenario_name`, presente tanto em `prompts.jsonl` quanto em `scenarios.jsonl`, representa uma **descrição de alto nível do cenário**, funcionando como um rótulo ou classe do problema (por exemplo, *kvm_network_responder_overload*). Esse campo é utilizado para identificação, organização e análise por categorias de falhas, mas **não deve ser interpretado como o diagnóstico causal**.

- O campo `diagnosis`, presente exclusivamente em `scenarios.jsonl`, descreve a **causa raiz específica da degradação de desempenho**, em nível técnico e operacional (por exemplo, *single-core CPU saturation due to network softirq processing*). Esse campo constitui o **ground truth** utilizado durante a avaliação dos modelos.

Ambos os campos referem-se ao mesmo cenário de falha, porém em níveis distintos de abstração: enquanto `scenario_name` identifica *o tipo de problema*, `diagnosis` explicita *o mecanismo causal subjacente*.

**Exemplo:**  
Um cenário identificado como `kvm_network_responder_overload` pode ter como diagnóstico causal específico a saturação de um único núcleo de CPU devido ao processamento de softirqs em uma configuração VirtIO de fila única. Embora os textos sejam diferentes, ambos descrevem o mesmo problema observado sob perspectivas complementares.


## Licença
CC-BY-4.0
