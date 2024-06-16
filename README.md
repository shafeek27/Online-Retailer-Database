This README file will provide an overview of the project, instructions on how to set up and run the code, and any other relevant details.

```markdown
# Online Retailer Database

This repository contains SQL scripts to create and populate an online retailer database with sample data. The database schema includes tables for suppliers, products, warehouses, and stock levels.

## Database Schema

The database schema consists of the following tables:

- `suppliers`: Stores supplier information.
- `products`: Stores product information, including a foreign key reference to the supplier.
- `warehouses`: Stores warehouse information.
- `stock_levels`: Tracks inventory levels for each product in each warehouse.

## Table Definitions

### Suppliers Table

```sql
CREATE TABLE suppliers (
    supplier_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    contact_name TEXT,
    phone_number TEXT,
    email TEXT
);
```

### Products Table

```sql
CREATE TABLE products (
    product_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    description TEXT,
    supplier_id INTEGER,
    FOREIGN KEY (supplier_id) REFERENCES suppliers(supplier_id)
);
```

### Warehouses Table

```sql
CREATE TABLE warehouses (
    warehouse_id INTEGER PRIMARY KEY AUTOINCREMENT,
    location TEXT NOT NULL,
    capacity INTEGER
);
```

### Stock Levels Table

```sql
CREATE TABLE stock_levels (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    product_id INTEGER,
    warehouse_id INTEGER,
    quantity INTEGER NOT NULL CHECK(quantity >= 0),
    last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES products(product_id),
    FOREIGN KEY (warehouse_id) REFERENCES warehouses(warehouse_id)
);
```

## Sample Data

The following sample data is inserted into the tables:

### Suppliers Data

```sql
INSERT INTO suppliers (name, contact_name, phone_number, email) VALUES
('Supplier A', 'John Doe', '1234567890', 'john.doe@example.com'),
('Supplier B', 'Jane Smith', '0987654321', 'jane.smith@example.com'),
('Supplier C', 'Alice Johnson', '1122334455', 'alice.johnson@example.com'),
('Supplier D', 'Bob Brown', '5566778899', 'bob.brown@example.com'),
('Supplier E', 'Charlie White', '0001112222', 'charlie.white@example.com');
```

### Products Data

```sql
INSERT INTO products (name, description, supplier_id) VALUES
('Product 1', 'Description of Product 1', 1),
('Product 2', 'Description of Product 2', 2),
('Product 3', 'Description of Product 3', 3),
('Product 4', 'Description of Product 4', 4),
('Product 5', 'Description of Product 5', 5),
('Product 6', 'Description of Product 6', 6),
('Product 7', 'Description of Product 7', 7),
('Product 8', 'Description of Product 8', 8),
('Product 9', 'Description of Product 9', 9),
('Product 10', 'Description of Product 10', 10);
```

### Warehouses Data

```sql
INSERT INTO warehouses (location, capacity) VALUES
('Warehouse 1', 10000),
('Warehouse 2', 15000),
('Warehouse 3', 20000),
('Warehouse 4', 25000),
('Warehouse 5', 30000),
('Warehouse 6', 35000),
('Warehouse 7', 40000),
('Warehouse 8', 45000),
('Warehouse 9', 50000),
('Warehouse 10', 55000);
```

### Stock Levels Data

```sql
INSERT INTO stock_levels (product_id, warehouse_id, quantity) VALUES
(1, 1, 50),
(2, 2, 75),
(3, 3, 100),
(4, 4, 125),
(5, 5, 150),
(6, 6, 175),
(7, 7, 200),
(8, 8, 225),
(9, 9, 250),
(10, 10, 275);
```

## Setup Instructions

To set up and run the database, follow these steps:

1. **Load the SQLite extension** in your JupyterLite notebook or environment:

    ```python
    %load_ext sql
    ```

2. **Connect to an SQLite database** (in-memory or file-based):

    ```python
    %sql sqlite:///:memory:  # For an in-memory database
    # or
    %sql sqlite:///your_database_name.db  # For a file-based database
    ```

3. **Create the tables** by executing the provided SQL commands.

4. **Insert the sample data** into the tables by executing the provided SQL commands.

## Contributing

If you have suggestions for improvements or find any issues, please feel free to open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

Save this README content to a file named `README.md` and include it in your GitHub repository. This file provides a comprehensive guide to understanding, setting up, and using the database code provided.
