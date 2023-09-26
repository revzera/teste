# Dicionários - AED2

## Alunos

* Jhonnatha Carvalho
* Kaike Ribas
* Lucas Martini
* Paulo Ricardo
* Ricardo Eliel

## Sumário

1. [Introdução](#introducao)
2. [O projeto em si](#projeto)
    
    2.1. [Estruturas de dados e Funções](#estrufuncdado)

    2.1.1. [Funções para Manipulação de Dados e cálculo do TF-IDF](#funcmanipulacao)

    2.2. [Tratamento das palavras](#tratamento)

    2.2.1 [*Stop Words*](#stopwords)

    2.3. [Função *Hash* e *Rerashing*](#hash)

3. [Estudo e resultados](#resultados)

    3.1. [](#)

4. [Conclusão](#conclusao)

*******

<div id='introducao'/>

## 1. Introdução

Em um mundo cada vez mais repleto de informações, a habilidade de localizar dados específicos em textos extensos torna-se crucial. Imagine-se diante de um densamente escrito livro, um documento longo ou até mesmo uma coleção de artigos, todos abarrotados de palavras e ideias. Nesse cenário, encontrar informações específicas ou identificar tópicos relevantes pode rapidamente se tornar uma tarefa desafiadora. É aí que entra a importância de ferramentas como o Índice Remissivo.

O Índice Remissivo desempenha um papel fundamental como um guia inteligente, organizando os termos e expressões encontrados em um texto e conectando-os às páginas correspondentes. Em essência, ele atua como um mapa que direciona os leitores a seções específicas do conteúdo, economizando tempo e simplificando a compreensão.

Um elemento-chave na construção desse índice é a identificação das chamadas "stop words", palavras comuns do idioma que, embora necessárias na comunicação cotidiana, geralmente não contribuem substancialmente para o entendimento de um texto. Estas incluem preposições, artigos, advérbios, números, pronomes e sinais de pontuação. O reconhecimento e tratamento adequado dessas palavras são fundamentais para garantir que o índice destaque os termos mais relevantes.

Além disso, introduzimos o conceito essencial de TF-IDF, uma métrica estatística que avalia a relevância de uma palavra em um documento em relação a um conjunto mais amplo de documentos. A sigla, que significa "Frequência do Termo - Inversa da Frequência no Documento", combina a frequência de uma palavra (TF) dentro do documento com sua raridade (IDF) em toda a coleção de documentos. O objetivo é identificar as palavras mais singulares e elucidativas no contexto do documento, tornando a compreensão e análise do conteúdo mais acessíveis.

Para calcular o TF-IDF, multiplicamos a frequência do termo (TF) pelo logaritmo da inversa da frequência no documento (IDF). O TF mede quantas vezes uma palavra ocorre em um documento específico, enquanto o IDF é determinado pelo logaritmo do número total de documentos dividido pelo número de documentos que contêm o termo em questão. As "stop words" são tratadas de forma neutra, uma vez que não contribuem significativamente para a relevância da palavra no contexto do documento.

Este projeto tem como objetivo central o desenvolvimento de um programa capaz de criar um índice remissivo a partir de um livro no formato de texto. Para alcançar essa meta, aplicaremos princípios de Tipos Abstratos de Dados (TAD) e técnicas de armazenamento, incluindo o uso de dicionários estáticos e dinâmicos. O resultado final será um conjunto de cinco páginas associadas a cada palavra identificada no livro, organizadas em ordem de relevância. Para garantir a eficiência e o desempenho do programa, tomaremos decisões apropriadas em relação às estruturas de dados e utilizaremos técnicas eficazes para o armazenamento e recuperação das informações necessárias.

Compreender as stop words, calcular o TF-IDF e construir um índice remissivo são etapas cruciais no processamento de texto e na busca eficaz de informações. Este projeto explora esses conceitos, oferecendo uma ferramenta valiosa para organizar e acessar o conhecimento contido em documentos extensos, beneficiando tanto os leitores ávidos quanto aqueles que buscam informações específicas em meio a um mar de palavras.

<div id='projeto'/>  

## 2. O projeto em si

Neste projeto, o objetivo principal é desenvolver um programa capaz de criar um índice remissivo a partir de um livro no formato de texto. Para atingir essa meta, serão aplicados princípios dos Tipos Abstratos de Dados (TAD) e técnicas de armazenamento, incluindo o uso de dicionários estáticos e dinâmicos. O resultado final incluirá um conjunto de cinco páginas associadas a cada palavra identificada no livro, organizadas em ordem de relevância.

<div id='estrudadofunc'/>

### 2.1 Estruturas de dados e Funções

<div id='estrufuncdado'/>

#### 2.1.1 Funções para Manipulação de Dados e cálculo do TF-IDF

Essas funções desempenham papéis específicos no processamento e análise dos dados do documento, permitindo a construção de métricas importantes, como o TF, IDF e TF-IDF, que são fundamentais para a análise de relevância de palavras e páginas em um contexto de processamento de texto e busca de informações, elas são:

   - ***n_containing_page*:** esta função é responsável por contar quantas vezes uma palavra ocorre em uma página específica. Ela percorre o dicionário dinâmico para obter as páginas em que a palavra ocorre e verifica se a página informada está na lista. Fundamental para calcular o TF-IDF posteriormente.

   -  ***n_containing*:** essa função conta quantas vezes uma palavra (identificada por sua chave) ocorre em todas as páginas. Ela é importante para calcular o IDF (Inverse Document Frequency) usado no cálculo do TF-IDF.
   - ***tf*:** calcula a frequência do termo (TF) de uma palavra em uma página específica. O TF mede a importância relativa de uma palavra em relação ao número total de palavras na página. Essa função é fundamental para calcular o TF de cada palavra em todas as páginas.

   - ***idf*:** calcula o Inverse Document Frequency (IDF) de uma palavra. O IDF é usado para avaliar a importância de uma palavra em todo o conjunto de documentos (páginas). Quanto menos frequente uma palavra for em todos os documentos, maior será seu IDF. 

   - ***tf_idf*:** calcula o TF-IDF (Term Frequency-Inverse Document Frequency) de uma palavra em uma página específica. O TF-IDF é uma métrica que combina o TF e o IDF e é usada para determinar a importância de uma palavra em relação a uma página e a todos os documentos. 

   - ***calcula_tf*:** essa função calcula o TF para todas as palavras em todas as páginas do documento. Ela percorre o dicionário dinâmico para obter as páginas em que cada palavra ocorre e calcula o TF para cada página. É crucial para ter o TF de todas as palavras nas páginas, preparando o terreno para o cálculo do TF-IDF.

   - ***calcula_idf*:** calcula o IDF de uma palavra específica usando o número total de páginas (qnt_paginas) e o número de páginas em que a palavra ocorre (n_containing). Essa função é importante para calcular o IDF de cada palavra, que é usado no cálculo do TF-IDF.

   - ***gerarChave*:** gera uma chave única para uma palavra com base no seu conteúdo. Isso é fundamental para indexar e recuperar informações sobre as palavras de maneira eficiente em estruturas de dados, como o dicionário dinâmico.

   Essas funções desempenham papéis específicos no processamento e análise dos dados do documento, permitindo a construção de métricas importantes, como o TF, IDF e TF-IDF, que são fundamentais para a análise de relevância de palavras e páginas em um contexto de processamento de texto e busca de informações.

<div id='tratamento'/>

#### 2.2. Tratamento das palavras



<div id='stopwords'/>

#### 2.2.1 *Stop Words*

 Como mencionado anteriormente, um aspecto importante do projeto é a criação e manipulação de palavras de parada. Essas funções desempenham um papel vital nesse processo:
   
   
   - ***struct* palavra**: esta estrutura é fundamental porque representa uma palavra no contexto do programa. Ela armazena a própria palavra como uma cadeia de caracteres (string) e uma chave associada a ela. A chave é geralmente gerada a partir do conteúdo da palavra e é usada para indexar e recuperar informações relacionadas à palavra de maneira eficiente em estruturas de dados.
   - ***struct* pagina**: ela armazena informações essenciais sobre a página, como o número da página e o número de ocorrências da palavra nessa página. Além disso, a estrutura inclui o valor TF (Frequência do Termo) da palavra na página, que é uma medida estatística crucial para determinar a relevância da palavra em uma página específica. Isso é fundamental para calcular o TF-IDF posteriormente.
   - ***struct* dados**: armazena informações abrangentes sobre o documento. Ela mantém o controle do número total de palavras e páginas no documento, além de incluir listas (como *listaPalavras* e *listaLinhas*) que permitem o armazenamento eficiente de informações relacionadas a palavras e páginas. Essa estrutura é central para o gerenciamento de dados e cálculos subsequentes.
   - ***struct* contador**: é importante porque rastreia a quantidade de palavras em uma página específica. Isso é necessário para calcular a frequência do termo (TF) de uma palavra em uma página e, consequentemente, o TF-IDF.
   - ***struct* nota**: é fundamental para armazenar informações sobre a relevância de uma palavra em relação a uma página específica. Ela inclui o valor TF-IDF da palavra nessa página, que é usado para classificar e identificar as palavras mais importantes no contexto do documento.

Este código tem como objetivo processar e tratar um arquivo de texto, realizando várias operações, como criação e manipulação de stop words, remoção de números e pontuações, conversão para letras minúsculas e geração de um novo arquivo de texto após o tratamento. Vou explicar as principais funcionalidades e o que cada função faz:

#### 2.1.2 Criando e manipulando *Stop Words* 

Um aspecto importante do projeto é a criação e manipulação de palavras de parada (stop words). Essas funções desempenham um papel vital nesse processo:

   - ***criar_sw*:** essa função cria uma nova stop word (palavra de parada) a partir de uma string passada como argumento e a aloca dinamicamente na memória. Retorna um ponteiro para a stop word criada.

   - ***imprimir_sw*:** Imprime uma stop word que é passada como um ponteiro genérico. É útil para depuração e visualização das stop words.

   - ***comparar_sw*:** compara duas stop words passadas como argumentos. Retorna um valor negativo se a primeira for menor, zero se forem iguais e um valor positivo se a primeira for maior. Essa função é usada para ordenar as stop words em uma estrutura de dados.

Função calcular o tamanho do livro:

   - ***tamanho_livro*:** abre o arquivo do livro (cujo nome é passado como argumento) e calcula o número total de palavras no livro. Retorna o tamanho do livro.

Função para Armazenar Stop Words em um Dicionário Estático:

   - ***guardar_sw*:** lê um arquivo de stop words (cujo nome é passado como argumento), cria stop words a partir das palavras lidas e as armazena em um dicionário estático (t_de). O dicionário é criado com base no tamanho do arquivo de stop words e nas funções de impressão e comparação de stop words. Retorna um ponteiro para o dicionário estático.

Funções para Tratar Palavras no Livro:

   - ***tratar_palavra*:** remove números e pontuações de uma palavra passada como argumento. Essa função é usada para limpar as palavras do livro.

   - ***to_lower_case*:** transforma todas as letras maiúsculas de uma palavra em letras minúsculas.

Funções para Tratar o Livro:

   - ***tratar_livro_sw*:** abre o arquivo do livro (cujo nome é passado como argumento), remove números e pontuações, converte letras maiúsculas em minúsculas e escreve o conteúdo tratado em um novo arquivo chamado "livro_processado.txt". Além disso, palavras presentes no dicionário de stop words (sw) são removidas do texto.

   - ***tratar_livro_art*:** funciona de maneira semelhante à função anterior, mas armazena as palavras removidas em um arquivo chamado "livro_auxiliar.txt". Isso implica que as palavras presentes no dicionário de stop words (art) não são removidas do texto, mas são copiadas para o arquivo auxiliar.

Essas funções, em conjunto, permitem processar e tratar um arquivo de texto, aplicando transformações nas palavras e removendo aquelas que estão no dicionário de stop words.

<div id='hashmap'/>

### 2.3. Função *Hash* e *Rerashing*

A função hash (hashing) pode ser aplicada no projeto para mapear as palavras identificadas no livro para um conjunto finito de índices em uma estrutura de dados conhecida como Dicionário Dinâmico. Cada palavra seria tratada como uma chave e passaria por essa função para determinar o índice em que deve ser armazenada na tabela de hash.

Por exemplo, ao processar uma palavra do livro, você pode aplicar uma função hash para calcular um índice com base no conteúdo da palavra. Essa função hash dividiria a palavra pelo tamanho da tabela de hash e retornaria o resto da divisão como o índice onde a palavra seria armazenada. Isso permitiria que você associasse eficientemente cada palavra a uma página ou a informações relevantes.

A função hash é fundamental para garantir uma distribuição uniforme das palavras na tabela de hash, minimizando colisões e permitindo o acesso eficiente às informações associadas a cada palavra.

Já o rehashing pode ser aplicado quando a tabela de hash atinge um fator de carga crítico, ou seja, quando está prestes a ficar cheia demais. Nesse ponto, você pode iniciar o processo de rehashing para redimensionar a tabela de hash e redistribuir as palavras.

Por exemplo, se o seu Dicionário Dinâmico estiver atingindo um fator de carga próximo a 1.0, isso significa que a tabela de hash está quase completamente cheia. Para evitar colisões excessivas e manter um bom desempenho, você pode iniciar o rehashing.

O rehashing envolveria a criação de uma nova tabela de hash com um tamanho maior, geralmente um número primo próximo do dobro do tamanho da tabela original. Em seguida, você iteraria pelas palavras na tabela original e, para cada palavra, calcularia um novo índice com base na função hash atualizada para a nova tabela. As palavras seriam então redistribuídas na nova tabela.

O rehashing é uma técnica importante para garantir que a tabela de hash mantenha um fator de carga aceitável, mesmo à medida que mais palavras são processadas. Isso evita que a tabela fique superlotada, o que pode levar a um desempenho ruim.

Em resumo, a função hash e o rehashing desempenham papéis essenciais no projeto, permitindo que as palavras do livro sejam eficientemente mapeadas e armazenadas em uma estrutura de dados que facilita a busca e recuperação de informações. Além disso, o rehashing garante que a estrutura de dados permaneça eficiente mesmo quando o número de palavras cresce.


<div id='resultados'/>

## 3. Estudo e resultados

--

<div id='conclusao'/>

## 4. Conclusão

--
