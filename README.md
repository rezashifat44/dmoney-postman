# DMoney API Tests

## What is DMoney?

DMoney is a mobile money (digital wallet) system. Admin, agent, customer and merchant users can hold balances and transfer money to each other, for example by cash-in from an agent, sending money between customers, cash-out, and payments to merchants. This repository holds a Newman/Postman suite that tests its main user and transaction flows through the API.

## Technology Used

- **Postman Collection (v2.1)**: API requests and test scripts in `collection/Assignment2_collection.json`
- **Newman**: command-line runner for the Postman collection
- **newman-reporter-htmlextra**: generates the HTML report
- **Node.js / npm**: runs the scripts and manages dependencies
- **Git**: version control

## Project Structure

```
Second Assignment/
├── collection/
│   └── Assignment2_collection.json   # Postman collection (requests + test scripts)
├── Reports/
│   └── .gitkeep                      # keeps the folder in git; report.html is generated here
├── report.js                         # Newman runner with the htmlextra reporter
├── package.json                      # dependencies and the npm test script
├── package-lock.json
├── CLAUDE.md                         # guidance for Claude Code (git-ignored)
└── README.md
```

`node_modules/`, `Reports/report.html` and `CLAUDE.md` are git-ignored.

## How to Run

### Prerequisites

- [Node.js](https://nodejs.org/) (LTS version) and npm. Check with:
  ```bash
  node -v
  npm -v
  ```
- Network access to the DMoney API server.

### Steps

1. **Clone the repository and open the project folder**
   ```bash
   git clone <repository-url>
   cd "Second Assignment"
   ```
2. **Install the dependencies**
   ```bash
   npm install
   ```
3. **Set the required variables.** The collection reads `baseURL` and `partnerKey` but never sets them. Add both as collection variables in `collection/Assignment2_collection.json`, either by editing them in Postman and re-exporting the collection, or by editing the `variable` section of the JSON. All other variables (tokens, user ids, phone numbers, email addresses) are set automatically during the run.
4. **Run the collection**
   ```bash
   npm test
   ```
   This runs `node report.js`, so you can use either command. The requests run in order, once: admin login, create users, activate users, log in as each user, then the transactions. The console prints "Collection run completed" when the run ends.
5. **View the report.** Open `Reports/report.html` in a browser.

### Run only part of the collection

```bash
npx newman run collection/Assignment2_collection.json --folder "Transaction"
```

Later folders depend on variables set by earlier ones, so running a folder alone will fail unless the variables it needs are already set.

## Documentation

API documentation: https://documenter.getpostman.com/view/18876113/2sBYHYtxpf

## Test Cases
https://docs.google.com/spreadsheets/d/1bNw7jQ__TcfVeqO1QMU9pRmN6VPgR82U0KmjoZrNv3Y/edit?usp=drive_link

## Summary

<img width="962" height="944" alt="image" src="https://github.com/user-attachments/assets/054b45d1-2d83-4f17-9a00-ad9a5aad7fd6" />
<img width="962" height="872" alt="image" src="https://github.com/user-attachments/assets/02dc581a-3bf6-4dc7-b19b-06963255d9ce" />

