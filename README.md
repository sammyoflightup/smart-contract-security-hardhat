# 🛡️ Smart Contract Security Audit (Using Hardhat)

This project demonstrates a step-by-step approach to auditing smart contracts using [Hardhat](https://hardhat.org/). It includes environment setup, contract development, test writing, vulnerability identification, and documentation with screenshots.

---

## 📁 Project Structure

```
smart-contract-security-hardhat/
├── contracts/           # Smart contract source files
├── scripts/             # Deployment scripts
├── test/                # Test cases (including security checks)
├── screenshots/         # Audit and testing screenshots
├── findings.md          # Documented vulnerabilities & analysis
├── README.md            # Project overview and guide
├── hardhat.config.js    # Hardhat configuration file
└── package.json         # Project dependencies
```

---

## 🧱 Step 1: Setup Hardhat

Install Hardhat and initiate the project:

```bash
mkdir smart-contract-security-hardhat
cd smart-contract-security-hardhat
npm init -y
npm install --save-dev hardhat
npx hardhat
```
Choose **"Create a basic sample project"** when prompted.

### Screenshot:
![Hardhat Setup](https://github.com/user-attachments/assets/a707dec3-a0df-4401-ab64-c509488b174f)

---

## 📜 Step 2: Write a Sample Contract

In `contracts/Sample.sol`:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Sample {
    uint256 public value;

    function setValue(uint256 _val) public {
        value = _val;
    }
}
```

---

## 🧪 Step 3: Write Test Cases (Including Vulnerability Checks)

In `test/Sample.js`:

```javascript
const { expect } = require("chai");

describe("Sample", function () {
  it("Should set the value correctly", async function () {
    const Sample = await ethers.getContractFactory("Sample");
    const sample = await Sample.deploy();
    await sample.deployed();

    await sample.setValue(10);
    expect(await sample.value()).to.equal(10);
  });
});
```

---

## 🧩 Step 4: Analyze and Document Findings

Create a `findings.md` file to note bugs and suggestions:

```
## 🐛 Finding 1: No Input Validation
- Function `setValue` accepts any number, including potential edge cases.
- 🔒 Recommendation: Add input validation to prevent malicious values.

## 🐛 Finding 2: Visibility Leakage
- No private/internal state.
- 🔒 Recommendation: Mark non-user-facing functions/variables appropriately.
```

---

## 📸 Audit Screenshots

| Screenshot | Description |
|-----------|-------------|
| ![Security Audit 1](https://github.com/user-attachments/assets/97169b3a-2709-4be2-80f7-4d6ee6498ba4) | Audit result overview |
| ![Sample](https://github.com/user-attachments/assets/33460d14-9082-4366-b7ec-deb7900ba4b6) | Testing logic flaws |
| ![Backend](https://github.com/user-attachments/assets/db13b245-11b9-43f1-8730-418af792cdf5) | Backend vulnerability assessment |
| ![33](https://github.com/user-attachments/assets/c2dcc079-2a97-4035-8181-78b3212d4566) | Contract behavior under fuzzing |
| ![22](https://github.com/user-attachments/assets/cf7e06d1-e85f-465b-9d84-f65bec6a925f) | Post-audit summary |

---

## 🚀 Run the Audit Tests

```bash
npx hardhat test
```

---

## 📬 Contributing

Feel free to fork this project, submit improvements, or log issues!

---

## 📄 License

MIT License

---

Let’s keep building secure contracts! 🛡️

