# FastAPI – The Comprehensive Study Guide

---

## 1. What is FastAPI?
FastAPI is a modern, high-performance Python web framework used to build RESTful APIs. It is designed to be fast, easy to use, and production-ready.

**FastAPI is built on:**
* **Starlette:** The ASGI web framework handling the web parts.
* **Pydantic:** Handling data validation and serialization.

It follows the **ASGI (Asynchronous Server Gateway Interface)** standard and natively supports asynchronous programming (`async`/`await`).



---

## 2. Why FastAPI?
* **Very high performance:** On par with NodeJS and Go.
* **Uses Python type hints:** Better editor support (autocompletion) and fewer bugs.
* **Automatic API documentation:** Generates docs as you write code.
* **Built-in validation:** Catch errors early with Pydantic.
* **Supports sync and async code:** Flexible for various workloads.
* **Easy testing:** Built-in support for testing clients.
* **Suitable for microservices:** Lightweight and fast.

---

## 3. Core Features of FastAPI
* **Automatic request validation:** Validates incoming data against your models.
* **Automatic response serialization:** Converts Python objects to JSON.
* **Dependency Injection:** Manage resources like database sessions easily.
* **Security utilities:** Built-in support for OAuth2 and JWT.
* **Background tasks:** Run processes after the response is sent.
* **Middleware support:** Intercept requests and responses.
* **WebSockets:** Real-time bi-directional communication.
* **SQL and NoSQL support:** Compatible with most databases.

---

## 4. Automatic Documentation
FastAPI automatically generates interactive documentation using **OpenAPI** and **JSON Schema**.

**Documentation endpoints:**
* `/docs`: Swagger UI (allows testing endpoints in the browser).
* `/redoc`: ReDoc (clean, organized documentation).
* `/openapi.json`: The raw OpenAPI schema.



---

## 5. Pydantic in FastAPI
FastAPI uses Pydantic models to define request and response data structures.

**Key Uses:**
* Validate input data types.
* Enforce data constraints.
* Serialize Python objects to JSON for responses.
* Generate automatic schemas.

**Example:**
```python
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str
```

---

## 6. JSON Schema
FastAPI automatically generates **JSON Schema** from your Pydantic models, path parameters, query parameters, and request bodies.

**JSON Schema is used to:**
* **Describe API structure:** Defines exactly what the data should look like.
* **Power Documentation:** It is the backbone of Swagger UI and ReDoc.
* **Enable Integration:** Allows frontend teams to know exactly what fields to send.
* **Client SDKs:** Can be used to automatically generate client-side code.

---

## 7. OpenAPI Specification
FastAPI fully follows the **OpenAPI** specification (formerly known as Swagger). 

**OpenAPI defines:**
* All available API endpoints and HTTP methods (GET, POST, etc.).
* Required and optional parameters.
* Request body structures and Response models.
* Authentication and Security schemes.

FastAPI automatically exposes the OpenAPI schema at the `/openapi.json` endpoint.

---

## 8. Authentication and Security
FastAPI provides integrated tools to handle security out of the box.

### 8.1 HTTP Basic Authentication
* Sends a username and password via HTTP headers.
* Simple to implement but generally used for internal/test environments.

### 8.2 OAuth2
* Supports **Password flow**, **Authorization code flow**, and **JWT (JSON Web Tokens)**.
* The standard choice for secure REST APIs and microservices.

### 8.3 API Key Authentication
* Keys can be passed via:
    * **HTTP Headers** (e.g., `X-API-Key`)
    * **Query Parameters**
    * **Cookies**
* Commonly used for service-to-service communication or rate-limiting public APIs.

---

## 9. Starlette Features Used by FastAPI
Since FastAPI is built on top of **Starlette**, it inherits several powerful features:

* **WebSocket Support:** For real-time, bi-directional communication (chat, live feeds).
* **GraphQL Support:** Easily integrated using Starlette-compatible libraries.
* **Background Tasks:** Allows you to run a function *after* returning the response (e.g., sending a welcome email).
* **Startup and Shutdown Events:** Useful for connecting to a database on start and closing it on exit.
* **Middleware:** Support for CORS, GZip compression, and custom request/response processing.
* **Static Files:** Ability to serve images, CSS, and JavaScript files directly.
* **Test Client:** A built-in tool (based on `httpx`) to test your endpoints without running a live server.



---

## 10. Database Support

### 10.1 SQL Databases
FastAPI works seamlessly with relational databases like **PostgreSQL, MySQL, and SQLite**.
* **Recommended Tools:** SQLAlchemy, SQLModel (built by the creator of FastAPI), or Tortoise ORM.

### 10.2 NoSQL Databases
Supports non-relational databases like **MongoDB, Redis, and Cassandra**.
* **Advantage:** Using asynchronous drivers (like Motor for MongoDB) allows for massive scalability and high performance.

---

## 11. GraphQL
FastAPI is not limited to REST. It can work alongside GraphQL:
* Allows for **REST + GraphQL hybrid APIs** in the same application.
* Provides flexible data querying where the client decides exactly what data they need.
* Usually implemented via libraries like **Strawberry** or **Ariadne**.