# 🚀 Go REST API with Gin Framework

This project is a simple REST API built using the [Gin](https://gin-gonic.com/) framework in Go. It provides endpoints to manage products in a database, including operations for listing, retrieving, creating, updating, and deleting products.

## ✨ Features

- **CRUD Operations**: Create, Read, Update, and Delete products 📝
- **MySQL Database Integration**: Uses GORM to connect and interact with a MySQL database 🗄️
- **JSON-based API**: Responses are provided in JSON format 📦
- **Auto-migration**: Automatically creates and updates the product table 🔄

## 🛠️ Prerequisites

- [Go](https://golang.org/dl/) version 1.23.1 or higher 🚀
- MySQL Database 🗄️
- (Optional) Docker for running MySQL locally 🐳

## 📦 Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/thoriqdharmawan/go-rest-api-gin.git
   cd go-rest-api-gin
   ```

2. Install the required Go modules:

   ```bash
   go mod tidy
   ```

3. Set up MySQL and create a database:

   ```sql
   CREATE DATABASE go_restapi_gin;
   ```

4. Update the MySQL connection string in `models/database.go`:
   ```go
   "root:root@tcp(localhost:3306)/go_restapi_gin"
   ```
   Replace `root:root` with your MySQL username and password.

## 🚀 Usage

1. Start the application:

   ```bash
   go run main.go
   ```

2. The API will be available at `http://localhost:8080` 🌐.

## 📋 API Endpoints

### 📄 List Products

- **Endpoint**: `GET /api/products`
- **Description**: Retrieve all products from the database.
- **Response**:
  ```json
  [
    {
      "id": 1,
      "nama_product": "Product 1",
      "deskripsi": "Description of Product 1"
    },
    ...
  ]
  ```

### 🔍 Get Product by ID

- **Endpoint**: `GET /api/products/:id`
- **Description**: Retrieve a specific product by its ID.
- **Response**:
  ```json
  {
    "id": 1,
    "nama_product": "Product 1",
    "deskripsi": "Description of Product 1"
  }
  ```

### ➕ Create Product

- **Endpoint**: `POST /api/products`
- **Description**: Create a new product.
- **Request Body**:
  ```json
  {
    "nama_product": "New Product",
    "deskripsi": "New Product Description"
  }
  ```
- **Response**:
  ```json
  {
    "id": 2,
    "nama_product": "New Product",
    "deskripsi": "New Product Description"
  }
  ```

### ✏️ Update Product

- **Endpoint**: `PUT /api/products/:id`
- **Description**: Update an existing product by its ID.
- **Request Body**:
  ```json
  {
    "nama_product": "Updated Product",
    "deskripsi": "Updated Description"
  }
  ```
- **Response**:
  ```json
  {
    "id": 1,
    "nama_product": "Updated Product",
    "deskripsi": "Updated Description"
  }
  ```

### 🗑️ Delete Product

- **Endpoint**: `DELETE /api/products`
- **Description**: Delete a product from the database.
- **Response**:
  ```json
  {
    "message": "Product deleted successfully"
  }
  ```

## 🛠️ Database Model

The product model used in this project:

```go
type Product struct {
    Id          int64  `gorm:"primaryKey" json:"id"`
    NamaProduct string `gorm:"type:varchar(300)" json:"nama_product"`
    Deskripsi   string `gorm:"type:text" json:"deskripsi"`
}
```

## 📚 Dependencies

This project uses the following Go packages:

- [Gin](https://github.com/gin-gonic/gin) v1.10.0: HTTP web framework.
- [GORM](https://gorm.io/) v1.25.12: ORM for Go.
- [Go MySQL Driver](https://github.com/go-sql-driver/mysql) v1.7.0: MySQL driver for Go.
