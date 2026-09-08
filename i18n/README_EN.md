# Payment Transaction Processing System with POS Terminal Emulation

> **Language:** English | [Русский](../README.md)

### 1) Participants:
- **Vladislav A. Bakin**, ASU-23-1b — [@Meidorislav](https://github.com/Meidorislav)
- **Angelina M. Umarova**, ASU-23-1b — [@gelya305](https://github.com/gelya305)

### 2) Project Topic:
**System for receiving and reliably processing payment transactions with POS terminal emulation**

### 3) Tasks:
- Development of a POS terminal emulator on Raspberry Pi (or equivalent): buttons/encoder for amount entry and operation confirmation, LED/display indication of transaction status (idle/processing/success/error).
- Publishing transaction events to Apache Kafka from multiple independent terminals for asynchronous, reliable delivery without blocking the source device.
- Development of a backend server in Go: Kafka consumer with idempotent transaction processing (deduplication by unique `transaction_id` via Redis), REST API for transaction status and history.
- Development of an Android application for the cashier (Java): real-time transaction status viewing and operation history.
- Load testing of the transaction processing pipeline.

### 4) Expected Result by December 2026:
A working prototype including:
- POS terminal emulator on Raspberry Pi (or equivalent);
- Kafka queue for transaction events;
- Go backend server with idempotent transaction processing;
- Android cashier application (Java) with transaction history and real-time status;
- Documented REST API (Swagger).

### 5) Repository Links:
The project consists of several components with different technology stacks and development lifecycles (Raspberry Pi payment terminal emulator, Go backend service, Java Android app) communicating via Kafka and REST API. Instead of a monorepo, a GitHub organization was chosen with a dedicated repository for each component — this simplifies independent builds, versioning, and CI/CD for each service:

- **GitHub Organization:** [https://github.com/pos-term](https://github.com/pos-term)
  - [pos-term/.github](https://github.com/pos-term/.github) — standard `.github` repository for the organization
  - [pos-term/term-emulator](https://github.com/pos-term/term-emulator) — POS terminal emulator
  - [pos-term/payment-processor](https://github.com/pos-term/payment-processor) — Go backend server
  - [pos-term/mobile-dashboard](https://github.com/pos-term/mobile-dashboard) — Cashier Android app
  - [pos-term/infra](https://github.com/pos-term/infra) — Infrastructure
