# Nike Store Entity Relationship Diagram (ERD)

This ERD models the data relationships in a Nike retail shoe store.

```mermaid
erDiagram
    PRODUCT {
        int product_id PK
        string name
        string model
        float price
    }

    CUSTOMER {
        int customer_id PK
        string name
        string email
        string phone
    }

    SALE {
        int sale_id PK
        int product_id FK
        int customer_id FK
        int quantity
        date sale_date
    }

    INVENTORY {
        int inventory_id PK
        int product_id FK
        int stock_quantity
        string location
    }

    PRODUCT ||--o{ SALE : contains
    CUSTOMER ||--o{ SALE : makes
    PRODUCT ||--|| INVENTORY : tracked_in
```

## Entity Descriptions

- **PRODUCT**: Stores details of each Nike shoe such as model name and price.
- **CUSTOMER**: Contains customer information for communication and purchase history.
- **SALE**: Records transactions showing which customer bought which product, in what quantity, and when.
- **INVENTORY**: Keeps stock records of each product, including location and quantity.

## Relationship Explanations

- A **PRODUCT** can be sold in many **SALE** transactions (1-to-many).
- A **CUSTOMER** can make many **SALE** transactions (1-to-many).
- Each **PRODUCT** has a single **INVENTORY** record showing current stock (1-to-1).

This ERD ensures that sales are tied to actual customers and available inventory, helping the store track performance and manage stock efficiently.

