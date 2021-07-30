Reprograma :rocket: | Turma Online 12 | Back-end | 2021 | Introdução ao Banco de Dados | Mongo db | Exercício prático


# Projeto Prático com Banco de Dados e Mongo db :dancers:

## Descrição do Projeto :capital_abcd: 

<p>Você deve criar um banco de dados novo (database) e uma coleção com um nome pertinente, de acordo com os dados e tema que você escolher. Os seguintes comandos devem ser feitos e entregues:

:small_blue_diamond: Inserção de documentos

:small_blue_diamond: Atualização de documentos

:small_blue_diamond: Exclusão de documentos

:small_blue_diamond: Consulta com projeção

:small_blue_diamond: Consulta utilizando 
combinação entre os seletores

:small_blue_diamond:Consulta paginada e ordenada (utilizar *skip*, *limit* e *sort*)<p>

## Comandos utilizados na resolução das demandas :arrow_forward:

Inicializei o mongo db através do Prompt de Comando do windows e inicializei a conexão com o Robot 3t, através da porta Reprograma local, criada em aula.

### Inserção de documentos na collection

Criei um arquivo .txt de séries que assisti durante a pandemia e inseri na collections que nomeei de series.

```
db.series.insertMany([
    {   
        "Nome": "Eu Nunca",
        "Ano": "2021",
        "Gênero": "Comédia",
        "Classificação etária": "14",
        "Quantidade de temporadas":  "2",
        "Sinopse": "Retrata a vida moderna e complicada de Devi, uma adolescente americana, filha de indianos e aluna nada popular na escola. A série é inspirada em momentos reais da infância da atriz e comediante Mindy Kaling."
    },
    {   
        "Nome": "A Cozinheira de Castamar",
        "Ano": "2021",
        "Gênero": "Drama",
        "Classificação etária": "16",
        "Quantidade de temporadas":  "1",
        "Sinopse": "O cozinheiro de Castamar é uma série dramática de época espanhola que adapta o romance homônimo de Fernando J. Muñez, estrelado por Michelle Jenner e Roberto Enríquez. Situado no início do século 18 em Madrid, o enredo segue a história de amor entre um cozinheiro agorafóbico e um nobre viúvo."
    },
    {   
        "Nome": "Mare of Easttown", 
        "Ano": "2021",
        "Gênero": "Drama Policial",
        "Classificação etária": "16",
        "Quantidade de temporadas":  "Minissérie",
        "Sinopse": "Uma detetive de uma pequena cidade investiga um assassinato local enquanto sua vida desmorona."
    },
    {   
        "Nome": "Outlander", 
        "Ano": "2014",
        "Gênero": "Drama",
        "Classificação etária": "16",
        "Quantidade de temporadas":  "5",
        "Sinopse": "Em 1945, em lua de mel na Escócia, a enfermeira em combate Claire Randall é misteriosamente transportada através do tempo para o ano de 1743."
    },
    {   
        "Nome": "The Handsmaid Tale", 
        "Ano": "2017",
        "Gênero": "Ficção científica",
        "Classificação etária": "17",
        "Quantidade de temporadas":  "4",
        "Sinopse": "Depois que um atentado terrorista tira a vida do presidente dos Estados Unidos e de grande parte dos outros políticos eleitos, uma facção católica toma o poder com o intuito de restaurar a paz."
    },
    {   
        "Nome": "Virgin River",
        "Ano": "2019",
        "Gênero": "Drama",
        "Classificação etária": "14",
        "Quantidade de temporadas":  "3",
        "Sinopse": "Uma enfermeira se muda de Los Angeles para uma cidadezinha no norte da Califórnia em busca de um recomeço. Mas a nova vida vai ser bem diferente do que ela imagina"
    },
    {   
        "Nome": "Sombra e Ossos", 
        "Ano": "2021",
        "Gênero": "Mistério",
        "Classificação etária": "14",
        "Quantidade de temporadas":  "1",
        "Sinopse": "Forças sinistras conspiram contra uma jovem depois dela revelar um poder capaz de unir seu mundo."
    },
    {   
        "Nome": "The Sinner", 
        "Ano": "2017",
        "Gênero": "Thriller",
        "Classificação etária": "16",
        "Quantidade de temporadas":  "3",
        "Sinopse": "The Sinner é uma série de antologia de drama policial norte-americana desenvolvida por Derek Simonds para a USA Network. O nome é uma homenagem ao romance de Petra Hammesfahr de 1999, que serviu de base para a primeira temporada."
    },
    {   
        "Nome": "Sex Life", 
        "Ano": "2021",
        "Gênero": "Dramas românticos para TV",
        "Classificação etária": "18",
        "Quantidade de temporadas": "1",
        "Sinopse": "Frustrada com o casamento morno, Billie começa e escrever um diário contando as histórias eróticas que viveu com o ex-namorado Brad."
    },
    {   
        "Nome": "Inacreditável", 
        "Ano": "2019",
        "Gênero": "Drama Policial",
        "Classificação etária": "16",
        "Quantidade de temporadas": "Minissérie",
        "Sinopse": "Uma jovem é acusada de fazer uma falsa denúncia de estupro. Anos depois, duas investigadoras seguem evidências que podem, finalmente, revelar a verdade."
    },
    {   
        "Nome": "The Morning Show", 
        "Ano": "2019",
        "Gênero": "Drama",
        "Classificação etária": "18",
        "Quantidade de temporadas": "1",
        "Sinopse": "The Morning Show é uma série de televisão americana de drama estrelada por Jennifer Aniston, Reese Witherspoon e Steve Carell, que estreou na Apple TV+ em 1 de novembro de 2019. A série é inspirada no livro Top of the Morning: Inside the Cutthroat World of Morning TV do jornalista Brian Stelter."
    }
])
```

### Atualização de documentos

```
db.getCollection('series').update(
    {
        "Nome": "A Cozinheira de Castamar"
    },
    
    {
        $set:{"Ano" : "2020"}
    }
  )
```

### Exclusão de documentos

```
db.series.remove({"Ano": "2020"})
```

### Consulta com projeção

Séries ordenadas do ano mais recente ao mais antigo.
```
db.getCollection("series").find().sort({"Ano": -1})
```
Séries ordenadas do ano mais antigo ao mais recente.
```
db.getCollection("series").find().sort({"Ano": 1})
```

### Consulta utilizando combinação entre os seletores
```
db.getCollection("series").find({"Gênero":"Drama","Ano":"2019"})
```
### Consulta paginada e ordenada

Consulta pela classificação etária, limitando em duas séries.
```
db.getCollection("series").find({"Classificação etária": "16"}).limit(2)
```