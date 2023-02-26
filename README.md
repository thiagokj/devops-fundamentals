# Fundamentos do Azure, Git, GitHub e DevOps

Projeto para aprendizado e revisão de conceitos.

## DevOps - Desenvolvimento e operações

Sustenta a infraestrutura das aplicações. Apto a publicar aplicações para produção.

## Git - Versionamento de Código

Git é um versionador de código (Source Control Manager).

- Compara documentos e faz merge (junção).
- Cria ramificações (branches) para varias versões da aplicação e posterior junção.
- Branches: uma versão para produção, outra versão para correção de bugs, etc.

Disponivel para baixar em [Git](https://git-scm.com/).

Para verificar a versão do Git execute **git --version**.

## GitHub - Plataforma

Fornece várias funcionalidades trabalhando sobre o Git. Serve para organizar os projetos.

É o portfólio dos desenvolvedores.

Para utilizar o GitHub via linha de comando (CLI), baixe o [GitHub CLI](https://cli.github.com/).

Verifique a versão com o comando **gh**.

## Repositórios

Local onde é armazenado código. Toda inteligência do Git é aplicada para criar versões
e permitir o trabalho em equipe.

Crie repositórios separando com traços. Ex: meu-primeiro-repo

Funções:

- Pin -> Fixa como favorito no seu perfil.
- Unwatch -> Indica se você quer receber notificações sobre alterações no repositório.
- Fork -> Cria uma cópia do projeto para o seu GitHub. As alterações não são enviadas para o projeto principal.
- Star -> Indica apoio ao projeto do Dev, gerando relevância e permitindo acompanhamento.

Explorando repositório:

- Code -> Todas as pastas e arquivos de repo.
- Issues -> Indicar problemas em um projeto, com rastreamento a cada interação.
- Pull requests -> Envia código para o GitHub.
- Actions -> Automação do repositório.
- Projects -> Gerenciamento do projeto.
- Wiki -> Documentação do projeto, como funcionalidades, regras de negócio e utilização.
- Security -> Segurança do projeto
- Insights -> Indicadores: Andamento do repo, quantidade commits, quem está trabalhando no projeto, etc.
- Settings -> Configurações do projeto: visibilidade, alterar o caminho, etc.

## Issues

É possivel abrir e acompanhar as solicitações (Issues), que possuem varias categorias como: bugs, documentação,
melhoria, questão, etc.

Assigners -> Direciona a issue para um usuario especifico.
Labels -> Categoria da issue.
Projects -> Faz referência ao projeto.
Milestones -> Faz referência a etapa do projeto.

## Projetos

Pode ser criado 1 projeto para o repositório ou 1 projeto para diversos repositórios.

Melhores praticas: Após criar o projeto, organize os boards de tarefas com uma visão ágil.

- Backlog -> Reune todas as idéias para o projeto.
- ToDo -> Tarefas a serem realizadas nas próximas semanas (15 dias aprox.).
- QA -> Verificação de qualidade, indicando que algo foi desenvolvido e aguarda publicação para produção.
- Done -> Tarefa concluída.

Vincule as issues ao projeto, que ficam com status **aguardando triagem** até ser indicado para qual
categoria do board ela pertence.

Se uma issue for muito grande (ex: criar um novo framework com IA), quebre a mesma em tarefas menores para
ficar mais fácil organizar.

## Milestones

Podem ser criadas etapas (milestones), agrupando as coleções de issues. Com os milestones, temos a estimativa de quando serão feitas as entregas e seus respectivos status. Ex: quando será corrigido botão de login.

É um indicador visual. O projeto **diz tudo que deve ser feito** e o milestone **diz quando deve ser feito**.

## Wiki

Toda documentação da aplicação pode ficar aqui. Evite informações confidenciais (sensíveis).

A Wiki é um bom local para documentar regras de negócio e processos, com passo a passo de como proceder ou
utilizar as ferramentas.

## Security

É possível criar politicas de segurança para o código enviado, com bots gerando alertas conforme critérios.

## Settings

Configurações referentes ao repo.

Collaborators -> Permissões de edição do repositório.
Branches -> Permissões de edição de ramificações.
Webhooks -> Integração com outros serviços como Discord. Ex: Automação para alterações no GitHub sendo enviadas para o Discord.
Discussions -> Habilita fórum para tirar dúvidas sobre o repositório.

## Fork

Retorna somente o código do projeto.

## Clonando repositório

Faça a autenticação no GitHub com o **gh auth login**

Para clonar o repositório use o comando **git clone urlDoProjetoNoGitHub**

Também é possivel alterar o nome da pasta local, adicionando ao comando **git clone urlDoProjetoNoGitHub NomeDaPasta**.

## Inicializando repositório

Utilize o comando **git init** para inicializar o repo local na branch principal (Main ou Master).

Para inicializar sempre na branch Main, utilize o comando **git config --global init.defaultBranch main**
esse comando afeta as configurações globais do Git.

Para definir seu nome de usuário gravado nas alterações e email utilize:

```Shell
git config --global user.name "Seu Nome e Sobrenome"
git config --global user.email "seuemail@dominio.sufixo"
```

Para recuperar esses dados utilize:

```Shell
git config --global user.name
git config --global user.email
```

## Enviando arquivos

1. Use o **git status** para verificar qual branch voce está e quais arquivos não estão rastreados no git.

1. Para adicionar arquivos, utilize o **git add nomeDoArquivo**. Agora o arquivo é rastreado pelo git.

Recomendação: A cada trabalho executado, faça um **commit**. Os commits são como checkpoints, onde é possivel voltar no caso de problemas.

1. O comando para salvar as alteração é o **git commit -m "Adicionado README"**.

1. Adicione o repositorio do GitHub com o comando:

```Shell
git remote add origin https://github.com/thiagokj/devops-fundamentals.git
```

Para enviar as alterações após executar o commit, faça o envio com o **git push -u origin main**
Obs: o parametro -u é Upstream (subir).

## Melhorias no envio

Para adicionar todos os arquivos de um projeto ao rastreio do git, utilize **git add --all**.

Crie um arquivo .gitignore para informar quais arquivos não devem ser enviados para o GitHub.

Comando: **dotnet new gitignore**

O arquivo gerado pelo dotnet é um padrão com as extensões e pastas comuns para não serem enviados.

Obs: Após a criação do arquivo, o controle é feito apenas para novos arquivos. Os arquivos já enviados
permanecem no repositório. A criação do .gitignore deve ser o primeiro ao iniciar o projeto.

## Removendo arquivos do GitHub

Execute o **git pull**. Todos os arquivos serão baixados do servidor para a maquina local.

Exclua as pastas e arquivos desnecessários. Execute o **git add --all** para adicionar as alterações.

Faça o **git commit -m "Organização de arquivos"**.

E envie as alterações com o **git push -u origin main**.

Obs: Ainda é possivel rastrear os commits anteriores no GitHub, e as informações antigas estão presentes.
Caso necessário, execute os comandos para limpar todo o histórico:

```Shell
git remote remove origin # Remove o repositorio remoto.
git checkout --orphan latest_branch # Altera a branch para uma alternativa.
git add --all # Adiciona todos arquivos e alterações ao git.
git commit -am "Edição Inicial" # Faz o git add e git commit juntos dos arquivos rastreados.
git branch -D main # Apaga a branch principal.
git branch -m main # Renomeia a branch alternativa para principal.
git remote add origin urlDoRepositorio # Adiciona o repositório remoto.
git push -f origin main # Envia todas as alterações para a branch principal no GitHub.
git gc --aggressive --prune=all # Apaga arquivos e pastas antigas.
```

## Branches

As branches são as ramificações.

**main** -> É a branch principal de produção. Deve ser evitado fazer commits na main.
O correto é criar uma branch paralela para fazer todas as alterações e só enviar o resultado final para main.

Para renomear uma branch use o comando **git branch -M novoNomeDaBranch**.

A criação de outras branches são feitas para resolver problemas ou novas funcionalidades da aplicação.

Para alternar entre branches, utilize **git checkout nomeDaBranch**.

Para criar uma nova branch, use **git checkout -b nome-da-branch**. Dessa forma é criada uma cópia da main.
