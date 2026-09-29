# Baozi Store API

API REST para o controle básico de clientes, produtos e pedidos da Baozi Store, uma pequena loja de pão chinês. Trabalho prático da disciplina de Desenvolvimento Web Back-End (UNINTER).

## Tecnologias

- Java 17
- Spring Boot 4.1.1
- Spring Data JPA (Hibernate)
- MySQL 8.0
- Maven
- Postman (testes)

## Estrutura do projeto

```
src/main/java/com/baozi/store
├── controller   # endpoints REST
├── model        # entidades JPA (Cliente, Produto, Pedido)
└── repository   # acesso ao banco (Spring Data JPA)
```

## Como executar

### Requisitos

- Java 17 ou superior
- MySQL 8 em execução na porta 3306

### Passo a passo

1. Clone o repositório:
```bash
   git clone https://github.com/rafaelasv/baozi-store-api.git
   cd baozi-store-api
```

2. Crie o banco de dados no MySQL:
```sql
   CREATE DATABASE baozi_store;
```
   As tabelas são criadas automaticamente pelo Hibernate ao iniciar a aplicação (`spring.jpa.hibernate.ddl-auto=update`).

3. Confira o usuário e a senha do MySQL em `src/main/resources/application.properties`. O padrão é usuário `root` e senha `admin`. Para usar outros valores, altere o arquivo ou defina as variáveis de ambiente `DB_USER` e `DB_PASSWORD`.

4. Execute a aplicação:
```bash
   # Windows
   .\mvnw spring-boot:run

   # Linux / macOS
   ./mvnw spring-boot:run
```

A API fica disponível em `http://localhost:8080`.

## Endpoints

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/clientes` | Cadastra um cliente |
| GET | `/clientes` | Lista todos os clientes |
| GET | `/clientes/{id}` | Consulta um cliente por ID |
| DELETE | `/clientes/{id}` | Apaga um cliente |
| POST | `/produtos` | Cadastra um produto |
| GET | `/produtos` | Lista todos os produtos |
| GET | `/produtos/{id}` | Consulta um produto por ID |
| DELETE | `/produtos/{id}` | Apaga um produto |
| POST | `/pedidos` | Registra um pedido |
| GET | `/pedidos` | Lista todos os pedidos |
| GET | `/pedidos/{id}` | Consulta um pedido por ID |
| DELETE | `/pedidos/{id}` | Apaga um pedido |

## Exemplos de requisições

Crie primeiro o cliente e o produto, porque o pedido depende deles.

**POST `/clientes`**
```json
{ "nome": "Rafaela5082512", "clienteDesde": "2026-09-28" }
```

**POST `/produtos`**
```json
{ "nome": "Baozi de carne", "preco": 6.50, "estoque": 100 }
```

**POST `/pedidos`**
```json
{ "cliente": { "id": 1 }, "produto": { "id": 1 }, "quantidade": 3 }
```

Se o cliente ou o produto informado no pedido não existir, a API responde `400 Bad Request`.

## Autora

Rafaela Silva Tavares, RU 5082512