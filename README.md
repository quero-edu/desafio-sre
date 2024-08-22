# Desafio SRE

## Arquitetura da aplicação
![Arquitetura app foo bar][https://github.com/user-attachments/assets/e02f4ec1-8b04-4138-99b6-c5dba0c18296]

## Executando o exemplo
Instalando o minikube
`curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64`
`sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64`

Subindo o cluster
`minikube start`

Instalando o addon necessário para o funcionamento do ingress
`minikube addons enable ingress`

Subindo o minikube dashboard
`minikube dashboard`

:warning: Garanta que você está executando o apply dentro do contexto do minikube, você pode confirmar isso rodando o senguinte comando `kubectl config current-context`. Caso esteja usando outro contexto você pode trocar usando o comando `kubectl config use-context minikube`

Agora você consegue subir a aplicação no seu minikube local usando o seguinte comando:
`kubectl apply -f foo-bar-app-example.yaml`

## Testando o exemplo
Pegue o ip do ingress para testar a aplicação, para isso basta executar:
`kubectl get ingress`

Abra seu navegar o testes as seguintes urls:
http://<ip_do_seu_ingress>/bar
http://<ip_do_seu_ingress>/foo


## Objetivo
Criar um chart helm para a aplicação kubernetes [foo-bar-app-example.yaml](foo-bar-app-example.yaml)
Para isso é importante que você entenda como funciona o kubernetes, seus comandos básicos e seus principais recusros (pod, service, deployment, secrets, etc...) e do helm 

## Requisitos minimos
* Chart helm funcionando
* O chart deve receber alguns argumentos para ser criado: 
    * nome do app foo
    * nome do app bar
    * porta do app foo
    * porta do app bar
    * imagem do app foo 
    * imagem do app bar

## Elevando o nível do seu desafio (opicional):
* Habilite o healthcheck (Dificuldade: :star:)
* Crie template de deployment para que a aplicação possa ser escalavél (Dificuldade: :star::star:)
* Crie template de secrets (Dificuldade: :star::star::star:)
* Crie template de HPA (Dificuldade: :star::star::star:)
* Crie tests para seu chart [DOC](https://helm.sh/docs/topics/chart_tests/) (Dificuldade: :star::star::star::star::star:)

[def]: image.png