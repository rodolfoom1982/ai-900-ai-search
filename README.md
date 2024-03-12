# AI-900: Azure Cognitive Search - Utilizando AI Search para Indexação e Consulta de Dados

<br>

## Índice

<br>

## Descrição do Projeto

Este projeto é um dos laboratórios do Bootcamp [Microsoft Azure AI Fundamentals](https://web.dio.me/track/microsoft-azure-ai-fundamentals), promovido através da parceria entre a Microsoft e a Dio.me.

Os alunos deste bootcamp tem, como principal objetivo, se prepararem para o exame de certificação Microsoft AI-900, dominando conceitos como visão computacional, classificação inteligente de imagem e inteligência de documentos com IA, enquanto se familiarizam com as tecnologias da Microsoft Azure.

Este desafio é o de número 4 do bootcamp e consiste na execução prática dos seguinte exercício:

- [Indexação no Azure AI](http://aka.ms/ai900-ai-search): explorar o serviço de índice de Pesquisa de IA do Azure

<br>

## Acessos necessários

Para realizar estes laboratórios, eu precisei criar uma [Subscrição do Microsoft Azure](https://azure.microsoft.com/)

A Microsoft permite criar uma subscrição de teste, na qual vários serviços podem ser experimentados gratuitamente por 12 meses, além de receber $200 para serem utilizados nos primeiros 30 dias.

<br>

## Introdução

O serviço de índice de Pesquisa de IA do Azure, conhecido como **Azure Cognitive Search**, oferece recursos de enriquecimento de IA para processar conteúdos que não são pesquisáveis em sua forma bruta.

Utilizando um conjunto de habilidades, ele pode traduzir textos, detectar idiomas, reconhecer entidades, extrair frases-chave e até realizar OCR em arquivos binários.

Além disso, o serviço suporta o enriquecimento incremental, que permite o uso de enriquecimentos em *cache* durante a execução do conjunto de habilidades, reduzindo assim os custos de processamento.

Para testar este serviço, utilizei uma base de avaliações de clientes de uma rede nacional de cafés (um dataset público que pode ser baixado [aqui](https://aka.ms/mslearn-coffee-reviews)).

Ao final, implementei uma solução de mineração de conhecimento que facilita a pesquisa de *insights* sobre as experiências do cliente, criando um índice de Pesquisa de IA do Azure.

Este experimento envolveu, entre outras, as seguintes etapas: extração de dados em um *datasource*, enriquecimento dos dados com habilidades de IA, utilização do indexador do Azure, consulta ao índice de pesquisa e revisão dos resultados salvos em uma base de conhecimento armazenada

<br>

## Aprovisionando os recursos necessários do Azure

Para realizar este laboratório, foi necessário aprovisionar, no [Portal do Azure](https://portal.azure.com/), os 3 serviços abaixo:

- ***Azure AI Search***: para gerenciará a indexação e a consulta;
- ***Azure AI services***: para enriquecer os dados na fonte de dados com *insights* gerados por IA;
- ***Storage Account***: para armazenar os documentos brutos

> [!NOTE]
> Os 3 serviços precisaram ser aprovisionados no mesmo local (região), para permitir a integração entre eles

1) Primeiramente, aprovisionei o ***Azure AI Search***, na região ***(US) East US***:

   > ![alt text](readmeFiles/gifs/001.gif)
   
   Confirmação do aprovisionamento concluído:
   
   > ![alt text](readmeFiles/images/002.png)

<br>

2) Em seguida, aprovisionei o ***Azure AI Search***, na mesma região:

   > ![alt text](readmeFiles/gifs/003.gif)
   
   Confirmação do aprovisionamento concluído:
   
   > ![alt text](readmeFiles/images/004.png)

<br>

3) Por fim, aprovsionei o ***Storage Account*** também em na região ***(US) East US***, conforme recomendação:

   > ![alt text](readmeFiles/gifs/005.gif)
   
   Confirmação do aprovisionamento concluído:
   
   > ![alt text](readmeFiles/images/006.png)
      
   Nota: Após aprovisionar o serviço, é necessário habilitar a opção que permite acesso anônimo ao serviço. Esta opção está dentro de ***Settings >>> Configuration***. Após selecionar a opção ***Enableb***, basta clicar no botão <kbd>Save</kbd>:
   
   > ![alt text](readmeFiles/images/007.png)

<br>

## Carregando os documentos no Azure Account

Como mencionado, utilizei um *dataset* público de clientes de uma rede de cafeteria. Caso queira conhecê-lo, disponibilizei-o aqui, dentro do projeto, em [inputs/reviews](inputs/reviews).

> [!Note]
> Nos serviço ***Storage Account***, será utilizado muito o termo ***blob*** (*Binary Large Object* ou Objeto Binário Grande), que nada mais é do que um dado não estruturado. Ele não está, necessariamente, em conformidade com nenhum formato de arquivo.

1) Criei um ***container*** para armazenar os *blobs*:



![alt text](readmeFiles/images/008.png)
![alt text](readmeFiles/images/009.png)
![alt text](readmeFiles/images/010.png)
![alt text](readmeFiles/images/011.png)
![alt text](readmeFiles/images/012.png)
![alt text](readmeFiles/images/013.png)
![alt text](readmeFiles/images/014.png)
![alt text](readmeFiles/images/015.png)
![alt text](readmeFiles/images/016.png)
![alt text](readmeFiles/images/017.png)
![alt text](readmeFiles/images/018.png)
![alt text](readmeFiles/images/019.png)
![alt text](readmeFiles/images/020.png)
![alt text](readmeFiles/images/021.png)
![alt text](readmeFiles/images/022.png)
![alt text](readmeFiles/images/023.png)
![alt text](readmeFiles/images/024.png)
![alt text](readmeFiles/images/025.png)
![alt text](readmeFiles/images/026.png)
![alt text](readmeFiles/images/027.png)
![alt text](readmeFiles/images/028.png)
![alt text](readmeFiles/images/029.png)
![alt text](readmeFiles/images/030.png)
![alt text](readmeFiles/images/031.png)
![alt text](readmeFiles/images/032.png)
![alt text](readmeFiles/images/033.png)
![alt text](readmeFiles/images/034.png)
![alt text](readmeFiles/images/035.png)
![alt text](readmeFiles/images/036.png)
![alt text](readmeFiles/images/037.png)
![alt text](readmeFiles/images/038.png)
![alt text](readmeFiles/images/039.png)
