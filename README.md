# 📝 API Mínima de Todo Items (.NET)

Esta é uma **API Mínima em .NET** desenvolvida com fins de **estudo e prática**, utilizando o padrão de **Minimal APIs** para gerenciamento de *Todo Items*.

O projeto demonstra conceitos importantes como:

* Minimal APIs
* DTOs (Data Transfer Objects)
* Organização de endpoints
* Versionamento simples de código
* Uso correto de `.gitignore`

---

## 🚀 Tecnologias Utilizadas

* **.NET (Minimal API)**
* **C#**
* **ASP.NET Core**

---

## 📁 Estrutura do Projeto

```text
APIMinima/
│
├── Program.cs
├── Todo.cs
├── TodoItemDTO.cs
└── APIMinima.csproj
```

### 📌 Descrição dos arquivos

* **Program.cs** → Configuração da aplicação e definição dos endpoints
* **Todo.cs** → Entidade principal do domínio
* **TodoItemDTO.cs** → DTO usado para retorno de dados (não expõe informações sensíveis)

---

## 📦 Modelo de Dados

Atualmente, os dados são manipulados **em memória**, sem persistência em banco de dados.

Como evolução natural do projeto, recomenda-se a integração com o **Entity Framework Core**, permitindo:

* Mapeamento objeto-relacional (ORM)
* Persistência dos dados
* Uso de migrations
* Maior organização da camada de dados

---

## 🧩 Entity Framework Core

O **Entity Framework Core (EF Core)** é o ORM oficial da Microsoft para aplicações .NET.

Em uma versão futura deste projeto, o EF Core poderá ser utilizado para:

* Criar o `DbContext`
* Mapear a entidade `Todo`
* Realizar operações CRUD no banco de dados
* Gerenciar migrations

Exemplo conceitual de um `DbContext`:

```csharp
public class AppDbContext : DbContext
{
    public DbSet<Todo> Todos { get; set; }

    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options)
    {
    }
}
```

---

## 📦 Modelo de Dados

### Todo

```json
{
  "id": 1,
  "name": "Estudar .NET",
  "isComplete": false,
  "secret": "123456"
}
```

> ⚠️ O campo `secret` é utilizado **apenas para fins didáticos**, simulando uma validação simples de acesso. **Não representa uma autenticação real**.

---

## 🔐 Sobre o "Secret"

O `Secret`:

* Não é JWT
* Não é API Key
* Não é autenticação profissional

Ele é apenas um campo enviado no **corpo da requisição** e validado manualmente no backend.

📌 Em projetos reais, o recomendado é:

* JWT Bearer Token
* API Key via Header
* OAuth / Identity

---

## 🔄 Endpoints

### ➕ Criar Todo Item

**POST** `/todoitems`

Body (JSON):

```json
{
  "name": "Estudar Minimal APIs",
  "isComplete": false,
  "secret": "123456"
}
```

---

### 📄 Listar Todo Items

**GET** `/todoitems`

---

### 🔍 Buscar Todo por ID

**GET** `/todoitems/{id}`

---

## 🧪 Testando com Postman

1. Abra o Postman
2. Escolha o método HTTP (GET ou POST)
3. Informe a URL da API (ex: `https://localhost:5001/todoitems`)
4. Para POST, envie o JSON no **Body → raw → JSON**

---

## ⚠️ Observações Importantes

* O projeto tem **finalidade educacional**
* Não deve ser usado em produção sem melhorias de segurança
* O `Secret` **não deve ser persistido em banco**

---

## 🧠 Próximos Passos (Evolução)

* Integração com **Entity Framework Core**
* Persistência dos dados em banco relacional (PostgreSQL ou SQL Server)
* Implementação de **DbContext** e **Migrations**
* Autenticação JWT
* Paginação
* Versionamento de API
* Filtros e validações

---

## 👨‍💻 Autor

**Paulo Vitor**
Estudante de Análise e Desenvolvimento de Sistemas
Foco em **C# .NET** e **Angular**

---

📌 *Projeto desenvolvido para aprendizado e consolidação de conceitos de APIs em .NET.*
