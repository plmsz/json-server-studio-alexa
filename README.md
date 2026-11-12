# 🚀 Fake API (`json-server`) — Studio Alexia Menezes

> 📌 **Nota do Projeto:** Este repositório serve como a **Fake API (REST API Mock)** da aplicação web do **Studio Alexia Menezes**, desenvolvida como Projeto de Extensão em Ciência da Computação. O modelo foi estruturado de forma genérica e reutilizável para que possa ser aproveitado como base em outros projetos.

---

## 🎯 Sobre o Projeto

Esta API fornece dados mockados via `json-server` para a aplicação web do **Studio Alexia Menezes**, cobrindo o gerenciamento e exibição de dados para:
- Serviços (sobrancelhas, cílios, unhas e estética facial)
- Agendamentos de clientes
- Horários de atendimento e informações do estúdio

---

## 📋 Sumário

- [Como configurar seu banco de dados](#-criando-seu-banco-de-dados-dbjson)
- [Executando localmente](#-executando-localmente)
- [Deploy no **Render**](#-deploy-no-render)
- [Deploy no **Azure**](#-deploy-no-azure)

---

## 🗄️ Criando seu banco de dados (`db.json`)

1. Clone este repositório para o seu computador:

```bash
git clone https://github.com/seu-usuario/json-server-studio-alexa.git 
cd json-server-studio-alexa

```

2. Edite o arquivo `db.json` com o seu conteúdo de acordo com a documentação do [`json-server`](https://github.com/typicode/json-server#example).

*Exemplo de estrutura no `db.json`:*

```json
{
  "servicos": [
    {
      "id": 1,
      "nome": "Design de Sobrancelhas",
      "categoria": "sobrancelhas",
      "preco": 50.0
    }
  ],
  "agendamentos": []
}

```

3. Salve o arquivo e faça o `commit` das suas alterações no Git.

---

## 💻 Executando Localmente

1. Instale as dependências:
```bash
npm install
# ou
yarn install
```


2. Inicie o servidor:
```bash
npm start
# ou
yarn start
```



O servidor estará disponível por padrão em `http://localhost:3000` (ou na porta definida pela variável de ambiente `PORT`).

---

## 🌐 Deploy no **Render**

O **[Render](https://render.com/)** é uma plataforma simples e gratuita para hospedagem de aplicações Node.js e APIs REST.

### Passo a Passo

1. Crie uma conta gratuita no [Render](https://render.com/).
2. No Dashboard do Render, clique no botão **New +** e selecione **Web Service**.
3. Conecte sua conta do GitHub e selecione o repositório deste projeto.
4. Preencha as configurações do serviço:
* **Name:** `json-server` (ou o nome de sua preferência)
* **Region:** Selecione a região mais próxima (ex: Oregon ou Ohio)
* **Branch:** `main` ou `master`
* **Runtime:** `Node`
* **Build Command:** `npm install` (ou `yarn`)
* **Start Command:** `node server.js` (ou `npm start`)
* **Instance Type:** `Free`


5. Clique em **Create Web Service**.

### 🔗 Configuração de Auto-Deploy via Webhook no GitHub
Para que o Render faça a implantação automaticamente sempre que você fizer um git push para o GitHub:

1. No painel do Render, vá nas configurações do seu serviço (Settings).

2. Na seção Deploy Hook, copie a URL gerada (ex: https://api.render.com/deploy/srv-...).

3. Acesse o repositório do seu projeto no GitHub.

4. Vá em Settings > Webhooks e clique em Add webhook.

5. Preencha os campos com as seguintes opções:

6. Payload URL: Cole a URL do Deploy Hook copiada do Render.

7. Content type: Altere para application/json.

8. Which events would you like to trigger this webhook?: Mantenha selecionado Just the push event.

9. Clique em Add webhook.

---

## ☁️ Deploy no **Azure**

Você também pode utilizar o **Microsoft Azure** para implantar sua API gratuitamente no plano App Service.

### Pré-requisitos e Instalação

1. Crie uma conta na [Azure](https://azure.microsoft.com/).
2. Instale a [Azure CLI](https://docs.microsoft.com/cli/azure/install-azure-cli) em seu computador.
3. Faça login no Azure pelo terminal:
```bash
az login
```



### Criando e Implantando o Projeto

1. Crie um grupo de recursos:
```bash
az group create -n MeuGrupoDeRecursos -l northeurope

```


2. Crie um plano de serviço:
```bash
az appservice plan create -n MeuPlanoDeServico -g MeuGrupoDeRecursos
```


3. Crie a Web App:
```bash
az webapp create -n NomeDaSuaApp -g MeuGrupoDeRecursos --plan MeuPlanoDeServico
```


4. Configurar o repositório de deploy Git local:
```bash
az webapp deployment source config-local-git -n NomeDaSuaApp -g MeuGrupoDeRecursos
```


5. Copie a URL gerada no passo anterior e adicione-a como um novo `remote` no seu repositório Git local:
```bash
git remote add azure <URL_RETORNADA>
```


6. Realize o push para o Azure:
```bash
git push azure master
```
