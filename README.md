# Deploy automatizado do Jenkins na Azure #

## Tecnologias utilizadas
1. Versionamento: GitHub;
2. Pipelines de CI/CD: GitHub Actions;
3. Infrastructure: Azure Container Instances;
4. Forma de Deploy da Aplicação: Container Docker;
5. Container Registry: dockerhub


## Configurações para o Deploy
1. Criar uma conta na Azure;
2. Criar um Resource Group com o nome "rg-jenkins" na região "Brazil South";
3. Recuperar as credenciais, executando o seguinte comando (substituindo a variável "subscription-id") no console disponível no portal da Azure:

```
az ad sp create-for-rbac --name "JenkinsApp" --role contributor --scopes /subscriptions/{subscription-id}/resourceGroups/rg-jenkins --sdk-auth
```

4. No Github, entrar nas settings do repositório e criar uma secret com o nome "AZURE_CREDENTIALS", colocando as quatro seguintes variáveis retornadas no comando do item 3.

```
{
  "clientId": "",
  "clientSecret": "",
  "subscriptionId": "",
  "tenantId": ""
}
```
5. Após o commit, aguardar a Github Action fazer o deploy e acessar o Jenkins em: http://renan-jenkins.brazilsouth.azurecontainer.io:8080/