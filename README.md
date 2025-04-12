# **MVP de Análise de Dados de Filmes do IMDB e TMDB com Arquitetura Lakehouse**
MVP de Eng. de Dados sobre Análise de Dados de Filmes do IMDB e TMDB

**Aluno: Victor Carlos Teixeira da Costa**

## **1. Descrição do Projeto**
Este projeto consiste no desenvolvimento de um pipeline de dados completo para análise de filmes, utilizando dados do IMDB (Internet Movie Database) e TMDB (The Movie Database). O objetivo principal é estruturar e processar esses dados em uma arquitetura Lakehouse de três camadas (Bronze, Prata e Ouro) para responder a perguntas de negócio relevantes sobre a indústria cinematográfica.

O pipeline abrange as seguintes etapas:

1. Coleta de Dados: Extração de dados brutos do IMDB e da API do TMDB.
2. Modelagem de Dados: Organização dos dados em um modelo Lakehouse, com camadas de refinamento progressivo.
3. Carga de Dados: Implementação de processos ETL (Extração, Transformação e Carga) para mover os dados entre as camadas.
5. Análise de Dados: Exploração e visualização dos dados para identificar tendências, padrões e insights sobre filmes.

## **2. Objetivos**

Este MVP busca responder às seguintes perguntas de negócio:

- Qual a relação entre o orçamento e o ROI (Retorno sobre Investimento) dos filmes?
- Como a popularidade dos gêneros cinematográficos evoluiu ao longo das décadas?
- Qual a tendência da duração dos filmes ao longo do tempo?
- Existe correlação entre a avaliação dos filmes e sua lucratividade?
- Quais são as colaborações mais frequentes entre diretores e atores?
- Como as características dos títulos dos filmes mudaram ao longo do tempo?

*Nem todos os objetivos foram atingidos completamente neste MVP, mas a base para futuras análises foi estabelecida.*

## **3. Plataforma**

O projeto foi desenvolvido principalmente na plataforma Microsoft Fabric, utilizando o ambiente Spark para processamento de dados. A escolha da plataforma foi motivada pela facilidade de uso, escalabilidade e integração com outras ferramentas de análise de dados.
- Versão do Spark: 3.5.1.5.4.20250211.1

## **4. Detalhamento das Etapas**
### **4.1. Busca pelos Dados**

Os dados utilizados neste projeto foram obtidos das seguintes fontes:
- **IMDB (Internet Movie Database)**: Datasets públicos disponíveis em datasets.imdbws.com
- Os seguintes datasets foram utilizados:
  - 'title.basics': Informações básicas sobre os títulos (filmes, séries, etc.).
  - 'title.ratings': Avaliações dos títulos.
  - 'title.crew': Informações sobre diretores e roteiristas.
  - 'name.basics': Informações sobre pessoas (atores, diretores, etc.).

- **TMDB (The Movie Database)**: API pública disponível em www.themoviedb.org. A API foi utilizada para obter informações adicionais sobre filmes, como:
  - Filmes populares.
  - Detalhes dos filmes (orçamento, receita, duração, etc.).
  - Créditos dos filmes (elenco e equipe).
  - Lista de gêneros.

### **4.2. Coleta**
A coleta de dados foi realizada através de scripts Python que baixam os datasets do IMDB e fazem requisições à API do TMDB. Os dados foram salvos no formato Delta Lake na camada Bronze do Lakehouse.

### **4.3. Modelagem**
Os dados foram organizados em um modelo Lakehouse com as seguintes camadas:

- Bronze: Camada de dados brutos, contendo os dados extraídos diretamente das fontes (IMDB e TMDB) sem nenhuma transformação.
- Prata: Camada de dados limpos e transformados, contendo os dados padronizados e enriquecidos.
- Ouro: Camada de dados agregados e modelados, contendo as visões analíticas específicas para responder às perguntas de negócio.

### **4.4. Carga**
A carga de dados foi realizada utilizando pipelines de ETL implementados em PySpark. Os pipelines realizam as seguintes transformações:
- Limpeza: Remoção de dados duplicados, tratamento de valores nulos e correção de inconsistências.
- Transformação: Conversão de tipos de dados, criação de novas colunas e agregação de dados.
- Enriquecimento: Junção de dados de diferentes fontes (IMDB e TMDB) para adicionar informações complementares.

### **4.5. Análise**
A análise de dados foi dividida em duas etapas:

### **4.5.1. Qualidade de Dados**
Foi realizada uma análise detalhada da qualidade dos dados em cada atributo, identificando problemas como:
- Valores nulos.
- Dados inconsistentes.
- Outliers.

As transformações realizadas nos pipelines de ETL visam corrigir esses problemas e garantir a qualidade dos dados para análise.

### **4.5.2. Solução do Problema**
Foram criados modelos analíticos específicos para responder às perguntas de negócio definidas nos objetivos. Os modelos utilizam SQL e PySpark para agregar, filtrar e transformar os dados.

**Resultados:**
Os modelos analíticos geraram insights valiosos sobre a indústria cinematográfica. Por exemplo, foi possível observar que:
- Filmes com orçamentos mais altos tendem a ter um ROI maior.
- Gêneros como animação e ficção científica são mais lucrativos em média.
- A duração dos filmes tem se mantido relativamente estável ao longo das décadas.
- Filmes com avaliações mais altas tendem a ter um sucesso comercial maior.

## **5. Código**
O código completo do projeto está disponível aqui neste repositório do GitHub.

## **6. Autoavaliação**
Durante o desenvolvimento deste MVP, enfrentei diversos desafios, como a complexidade da integração de dados de diferentes fontes e a necessidade de otimizar os pipelines de ETL para garantir o desempenho.

Apesar dos desafios, consegui atingir os objetivos principais do projeto, que eram:
- Estruturar e processar dados do IMDB e TMDB em uma arquitetura Lakehouse.
- Implementar processos ETL para mover os dados entre as camadas.
- Criar modelos analíticos para responder a perguntas de negócio relevantes.

No entanto, alguns objetivos não foram atingidos completamente, como a análise das colaborações entre diretores e atores e a análise das características dos títulos dos filmes ao longo do tempo.

Para trabalhos futuros, pretendo:
- Aprofundar a análise dos dados, explorando novas perguntas de negócio.
- Implementar pipelines de ETL mais robustos e eficientes.
- Criar visualizações interativas para facilitar a exploração dos dados.
- Integrar os dados com outras fontes de dados para enriquecer a análise.
