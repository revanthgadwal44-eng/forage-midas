# JPMorgan Chase & Co. – Advanced Software Engineering Virtual Experience

## Overview

This project was completed as part of the JPMorgan Chase & Co. Advanced Software Engineering Virtual Experience Program hosted on Forage.

The application simulates a backend financial transaction processing system built using Spring Boot, Apache Kafka, REST APIs, and an H2 in-memory database.

The system:
- Consumes transactions from Kafka
- Validates and processes transactions
- Stores transaction history in a database
- Integrates with an external Incentive API
- Exposes REST endpoints for querying balances

---

## Technologies Used

- Java 17
- Spring Boot 3.2.5
- Apache Kafka
- Spring Kafka
- Spring Data JPA
- H2 Database
- REST APIs
- Maven
- JUnit 5
- Testcontainers

---

## Features

### Kafka Transaction Processing
- Consumes transaction messages from Kafka topic:
  - `trader-updates`
- Uses JSON serialization/deserialization with Spring Kafka

### Transaction Validation
Transactions are processed only if:
- Sender exists
- Recipient exists
- Sender has sufficient balance

### Database Integration
- Stores users and transaction records using H2 database
- Uses JPA/Hibernate entities and repositories

### Incentive API Integration
- Integrates with an external Incentive API running on:
  - `http://localhost:8080/incentive`
- Incentive amount is added to recipient balance

### Balance REST API
Exposes endpoint:

```http
GET /balance?userId={id}
```

Returns the current user balance as JSON.

Application runs on:

```text
http://localhost:33400
```

---

## Project Structure

```text
src/main/java/com/jpmc/midascore
│
├── component
│   └── DatabaseConduit.java
│
├── controller
│   └── BalanceController.java
│
├── entity
│   ├── UserRecord.java
│   └── TransactionRecord.java
│
├── foundation
│   ├── Balance.java
│   └── Transaction.java
│
├── repository
│   ├── UserRepository.java
│   └── TransactionRepository.java
│
└── MidasCoreApplication.java
```

---

## Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/your-username/forage-midas.git
cd forage-midas
```

### 2. Install Java 17

Verify installation:

```bash
java -version
```

### 3. Start Incentive API

```bash
java -jar services/transaction-incentive-api.jar
```

### 4. Run Application

```bash
mvn spring-boot:run
```

### 5. Run Tests

```bash
mvn test
```

---

## Kafka Configuration

Configured in `application.yml`:

```yaml
general:
  kafka-topic: trader-updates

server:
  port: 33400
```

---

## Learning Outcomes

This project strengthened understanding of:

- Event-driven architecture
- Apache Kafka messaging systems
- Spring Boot backend development
- REST API design
- Database persistence with JPA/Hibernate
- Integration testing
- Microservice communication
- Debugging distributed systems

---

## Author

**Revanth Gadwal**

Completed as part of the JPMorgan Chase & Co. Forage Virtual Experience Program.
