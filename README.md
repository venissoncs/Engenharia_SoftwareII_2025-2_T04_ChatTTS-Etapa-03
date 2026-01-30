# Engenharia_SoftwareII_2025-2_T04_ChatTTS-Etapa-03
GRUPO 5:

01 - Filippi Reis Menezes - 202300027230
02 - Jackson Santana Carvalho Júnior - 202300027365 03- Gabriel Bastos Pimentel - 202300061590
04- Marcos Vinícius Dantas Aguiar - 201800084345 05- Caio Victor Prado Cruz - 202100011234
06- Yan Victor Araujo do Nascimento - 202100046006 07- Leonardo de Souza Aragão - 202200117002
08 - Vênisson Cardoso Dos Santos – 201700063182


Responsáveis pela investigação: 01 - Filippi Reis Menezes
02 - Jackson Santana Carvalho Júnior
04 - Marcos Vinícius Dantas Aguiar 05 - Caio Victor Prado Cruz


Responsáveis por localizar as evidências: 07- Leonardo de Souza Aragão
06- Yan Victor Araujo do Nascimento 03- Gabriel Bastos Pimentel
08 - Vênisson Cardoso Dos Santos

Descrição:

O ChatTTS é um sistema de conversão de texto em fala (Text-to-Speech) de código aberto, especificamente otimizado para cenários de conversação, como diálogos em LLMs ou assistentes virtuais. O seu diferencial é a otimização para conversação natural, sendo capaz de reproduzir nuances da fala humana (como pausas e risos) em diálogos para assistentes virtuais e LLMs. É um projeto mantido de forma colaborativa pela comunidade no GitHub.

    1. Diagnósticos

A investigação no repositório ChatTTS revelou que o projeto já possui um nível intermediário de automação, utilizando o GitHub Actions como ferramenta principal de CI/CD. Durante a auditoria, foram localizadas evidências de diversos fluxos configurados na pasta .github/workflows, que visam padronizar o código e garantir a integridade das contribuições.
Os principais componentes identificados foram:
    • Validação de Qualidade e Testes: O arquivo unitest.yml executa testes unitários em diferentes versões de Python, enquanto o pull-format.yml e o push-format.yml verificam a padronização do código.
    • Gestão de Lançamentos: Existe um fluxo automatizado (upload-pypi.yml) para publicação de pacotes no PyPI via tags de versão.
    • Manutenção: Automações secundárias, como close-issue.yml para fechar tarefas obsoletas e checksum.yml para integridade de modelos, também estão presentes.
Apesar da presença dessas ferramentas, o diagnóstico aponta que a automação está fragmentada. Não há um pipeline centralizado que conecte todas as etapas de forma linear, e o processo ainda depende fortemente de validações manuais por parte dos mantenedores antes que o código seja integrado à branch principal. Isso gera gargalos no tempo de resposta e aumenta o risco de falha humana, pois não há garantia de que todos os testes foram cobertos de forma sistêmica antes da revisão humana.
        1.1 Metodologia

Para a realização da Etapa 1, a equipe seguiu um protocolo de auditoria de DevOps dividido em quatro fases principais. Este roteiro pode ser utilizado para replicar a análise em qualquer repositório de software.
Passo 1: Identificação e Contextualização do Objeto
O primeiro passo consiste em selecionar um projeto Open Source e compreender sua finalidade.
            ▪ Ação: Acessar o repositório oficial (no nosso caso, o ChatTTS) e identificar a linguagem principal (Python) e a área de atuação (Sintese de voz/AI).
            ▪ Documentação: Registrar o nome do projeto, link original e uma breve descrição das suas funcionalidades.
Passo 2: Investigação de Infraestrutura de CI/CD
Nesta fase, busca-se entender se o projeto já possui mecanismos de automação.
            ▪ Varredura de Diretórios: Navegar pela estrutura de arquivos à procura da pasta .github/workflows. A existência desta pasta confirma o uso do GitHub Actions.
            ▪ Análise de Histórico: Acessar a aba "Actions" no GitHub para verificar o histórico de execuções. É necessário observar se os runs (execuções) são frequentes e se costumam terminar em sucesso (verde) ou falha (vermelho).
Passo 3: Auditoria Técnica dos Workflows (Arquivos YAML)
Após localizar os arquivos, deve-se abrir e analisar cada arquivo .yml para entender o que está sendo automatizado. No caso do ChatTTS, auditamos:
            ▪ unitest.yml: Verifica a execução de testes unitários.
            ▪ pull-format.yml e push-format.yml: Verificam a padronização e estilo do código.
            ▪ upload-pypi.yml: Automatiza o deploy para o gerenciador de pacotes.
            ▪ Evidências: Capturar prints das telas do GitHub que comprovam a existência e o conteúdo desses arquivos.
Passo 4: Mapeamento de Fluxo e Identificação de Gargalos
Com os dados coletados, deve-se cruzar a automação existente com o processo de contribuição (Pull Requests).
            ▪ Criação do Diagrama AS-IS: Desenhar o fluxo que o código percorre desde o desenvolvedor local até o merge final, destacando onde a automação atua e onde o processo para.
            ▪ Diagnóstico Crítico: Identificar falhas. No ChatTTS, observamos que, apesar de haver testes, o processo ainda é fragmentado e depende de revisões manuais obrigatórias para o merge, o que caracteriza um gargalo de agilidade e um risco de falha humana.
