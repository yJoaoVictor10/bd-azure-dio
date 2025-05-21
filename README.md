# Configuração de uma Instância de Banco de Dados na Azure ☁️🗄️

## 📄 Descrição do Projeto

Este projeto tem como objetivo demonstrar o processo de configuração de uma instância de banco de dados na **Microsoft Azure**, utilizando os conhecimentos adquiridos na plataforma **DIO - Digital Innovation One**. Este README documenta os passos realizados e os conceitos aplicados no provisionamento e gerenciamento de um banco de dados na nuvem.

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

- ☁️ **Microsoft Azure**
- 🗄️ **Azure SQL Database** (Modelo PaaS)
- 🔒 **Firewall Rules (IP Whitelisting)**
- 🧠 **SQL Server Management Studio (SSMS)** ou **Azure Data Studio**
- 🗂️ **SQL Query Language (T-SQL)**
- 📝 **Git e GitHub** (para versionamento e documentação)

---

## 🏗️ Etapas da Configuração

### 1️⃣ Acesso ao Portal Azure

- Acesse: [https://portal.azure.com](https://portal.azure.com)
- Realize o login com sua conta da Microsoft.

### 2️⃣ Criação do Grupo de Recursos

- No menu lateral, selecione **"Grupos de Recursos"**.
- Clique em **“Criar”** e configure:
  - **Nome:** `grupo-banco-dio`
  - **Região:** (ex.: *Brazil South*)

### 3️⃣ Criação da Instância de Banco de Dados SQL

- Acesse **"SQL Databases"**.
- Clique em **“Criar”** e preencha:
  - **Assinatura:** (Escolha a sua)
  - **Grupo de recursos:** `grupo-banco-dio`
  - **Nome do banco:** `bd-dio`
  - **Servidor:** Criar novo servidor
    - **Nome do servidor:** `servidorbd-dio`
    - **Login do administrador:** `adminbd`
    - **Senha:** (sua senha segura)
    - **Localização:** (ex.: *Brazil South*)
- **Configurações do banco:** Plano básico (para estudo).
- Clique em **"Revisar + criar"** e depois **"Criar"**.

### 4️⃣ Configuração do Firewall

- Após a implantação:
  - Vá até **"Configurações de firewall e redes virtuais"**.
  - Adicione o seu IP atual para permitir acesso externo.
  - Opcional: libere para outros IPs, como servidores, colegas ou ambientes de teste.

### 5️⃣ Conexão ao Banco de Dados

- Utilize o **SQL Server Management Studio (SSMS)** ou **Azure Data Studio**.
- Dados de conexão:
  - **Servidor:** `servidorbd-dio.database.windows.net`
  - **Login:** `adminbd`
  - **Senha:** (a definida anteriormente)
  - **Banco de dados:** `bd-dio`

### 6️⃣ Criação e Manipulação de Dados

#### Script de exemplo:

```sql
CREATE TABLE Clientes (
    ID INT PRIMARY KEY IDENTITY(1,1),
    Nome NVARCHAR(100) NOT NULL,
    Email NVARCHAR(100) UNIQUE NOT NULL,
    DataCadastro DATE DEFAULT GETDATE()
);

INSERT INTO Clientes (Nome, Email) VALUES
('João Silva', 'joao@email.com'),
('Maria Souza', 'maria@email.com');

SELECT * FROM Clientes;
