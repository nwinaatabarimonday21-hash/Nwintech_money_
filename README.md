# NwinTech Money — backend-enabled demo

This project includes an Express API, PostgreSQL storage, hashed passwords, signed short-lived JWTs, per-user wallets, transaction records, and a mobile-friendly frontend.

## Important limits
This is a **demo only**. It uses fictional exchange rates and simulated deposits/withdrawals. It does not issue foreign receiving accounts or send bank transfers. Do not accept customer funds or use this as a live financial service without an appropriately authorised provider, regulatory/legal review, KYC/AML controls, reconciliation, monitoring, and a security review.

## Run locally
1. Install Node.js 20+ and PostgreSQL.
2. Create a PostgreSQL database, e.g. `nwintech`.
3. Copy `.env.example` to `.env`.
4. Set `DATABASE_URL` and a random `JWT_SECRET` of at least 32 characters.
5. Run:
   ```bash
   npm install
   npm start
   ```
6. Open `http://localhost:3000`.

## Deploy to Render
1. Upload this folder to a new GitHub repository.
2. Sign in to Render and create a Blueprint from that repository (it reads `render.yaml`).
3. Wait for the web service and PostgreSQL database to finish deploying.
4. Open the Render service URL and test registration.
5. Keep `DEMO_MODE=true` while testing. Never set up real money movement by simply changing this flag; the code intentionally has no real payment-provider integration.

## API routes
- `GET /api/health`
- `GET /api/config`
- `POST /api/auth/register` `{name,email,password}`
- `POST /api/auth/login` `{email,password}`
- `GET /api/me` (Bearer token)
- `POST /api/demo/deposit` `{currency,amount}` (demo only)
- `POST /api/convert` `{from,to,amount}` (demo only)
- `POST /api/withdrawals` `{bank,amount}` (records simulated withdrawal only)

## Before any real-money launch
Implement provider-issued receiving account details, verified provider webhooks, idempotency keys, ledger-based accounting, reconciliation, limits and fraud controls, KYC/AML/sanctions checks, audit trails, secure session/refresh-token strategy, email verification and password reset, monitoring/backups, privacy policy and terms, and a documented compliance/legal review. Never trust a browser request as proof of a deposit.
