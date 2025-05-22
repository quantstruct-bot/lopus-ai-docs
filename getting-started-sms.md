# Getting Started: Sending Your First SMS with a1base

This guide will help you send your first SMS using the a1base API. Code examples are provided in both Python and TypeScript.

---

## Prerequisites
- Your a1base `accountId`
- Your API credentials: `x-api-key` and `x-api-secret`
- The sender and recipient phone numbers (in international format)

---

## API Endpoint
```
POST /v1/messages/sms/{accountId}/send
```

### Request Headers
- `x-api-key`: Your API key
- `x-api-secret`: Your API secret

### Request Body (JSON)
```
{
  "content": "Hello from a1base!",
  "from": "+1234567890",
  "to": "+1098765432",
  "service": "sms"
}
```

---

## Python Example
```python
import requests

API_URL = "https://api.a1base.com/v1/messages/sms/{accountId}/send"
ACCOUNT_ID = "your_account_id"
API_KEY = "your_api_key"
API_SECRET = "your_api_secret"

headers = {
    "x-api-key": API_KEY,
    "x-api-secret": API_SECRET,
    "Content-Type": "application/json"
}

payload = {
    "content": "Hello from a1base!",
    "from": "+1234567890",
    "to": "+1098765432",
    "service": "sms"
}

response = requests.post(
    API_URL.format(accountId=ACCOUNT_ID),
    headers=headers,
    json=payload
)

print(response.json())
```

---

## TypeScript Example
```typescript
import axios from 'axios';

const API_URL = 'https://api.a1base.com/v1/messages/sms/{accountId}/send';
const ACCOUNT_ID = 'your_account_id';
const API_KEY = 'your_api_key';
const API_SECRET = 'your_api_secret';

const headers = {
  'x-api-key': API_KEY,
  'x-api-secret': API_SECRET,
  'Content-Type': 'application/json',
};

const payload = {
  content: 'Hello from a1base!',
  from: '+1234567890',
  to: '+1098765432',
  service: 'sms',
};

axios.post(
  API_URL.replace('{accountId}', ACCOUNT_ID),
  payload,
  { headers }
).then(res => {
  console.log(res.data);
}).catch(err => {
  console.error(err);
});
```

---

## Response
A successful request will return:
```
{
  "to": "+1098765432",
  "from": "+1234567890",
  "body": "Hello from a1base!",
  "status": "queued"
}
```

---

## Next Steps
- Check your webhook endpoint for delivery status updates.
- Explore the API documentation for more features (media, group messages, etc).
