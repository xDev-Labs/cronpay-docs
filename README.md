## CronPay - API Docs

Learn how to integrate CronPay API to create transactions and check their status.

## 📚 API Documentation

### 🔑 Getting API Keys

To use the CronPay API, you need to obtain an API key from the [CronPay Developer Dashboard](https://app.cronpay.xyz/keys).

---

### 1. Create Transaction

Create a new transaction by sending a POST request with your API key, currency, and amount.

**Endpoint**

```
POST https://gateway.cronpay.xyz/api/create-transaction
```

**Request Example**

```bash
curl --location 'https://gateway.cronpay.xyz/api/create-transaction' \
--header 'Content-Type: application/json' \
--data '{
    "apikey": "cronpay_api_key",
    "currency": "INR",
    "amount": 100
}'
```

**Parameters**

| Parameter  | Type   | Description                    |
| ---------- | ------ | ------------------------------ |
| `apikey`   | string | Your CronPay API key           |
| `currency` | string | Currency code (e.g., INR, USD) |
| `amount`   | number | Transaction amount             |

**Response**

```json
{
  "id": "16f0d91f-d790-4e5d-95b2-e46b118b29d1"
}
```

Returns a unique transaction ID that can be used to check the transaction status.

---

### 2. Get Transaction Status

Check the status of a transaction using the transaction ID returned from the create transaction endpoint.

**Endpoint**

```
POST https://gateway.cronpay.xyz/api/transaction-status
```

**Request Example**

```bash
curl --location 'https://gateway.cronpay.xyz/api/transaction-status' \
--header 'Content-Type: application/json' \
--data '{
    "apikey": "cronpay_api_key",
    "transaction_id": "16f0d91f-d790-4e5d-95b2-e46b118b29d1"
}'
```

**Parameters**

| Parameter        | Type   | Description                                |
| ---------------- | ------ | ------------------------------------------ |
| `apikey`         | string | Your CronPay API key                       |
| `transaction_id` | string | The transaction ID from create transaction |

**Response**

```json
{
  "id": "16f0d91f-d790-4e5d-95b2-e46b118b29d1",
  "status": "completed"
}
```

**Status Values**: `completed`, `pending`, or `failed`

---

### ⚠️ Important Notes

- Make sure to replace `cronpay_api_key` with your actual API key from the [Keys](https://app.cronpay.xyz/keys) page
- All requests must include `Content-Type: application/json` header
- Store your API keys securely and never expose them in client-side code

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
