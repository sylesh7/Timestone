# TimeStone - Quantum-Resistant Time Capsule Platform

TimeStone is a decentralized time capsule platform that combines quantum-resistant encryption, blockchain technology, and IPFS storage to create secure, time-locked digital memories. The platform uses post-quantum cryptography (Kyber-768) to ensure digital assets remain secure against future quantum computing threats.

## Architecture Overview

The TimeStone platform consists of five main components:

### 1. Frontend (Next.js + React)
- Modern, responsive web interface with 3D animations
- Wallet integration (RainbowKit + Wagmi)
- Real-time dashboard for capsule management
- Drag-and-drop file upload with multimedia support

### 2. Backend (Node.js + Express)
- Post-quantum encryption service (Kyber-768)
- IPFS integration for decentralized storage
- RESTful API for frontend communication
- Time capsule metadata management

### 3. Smart Contracts (Etherlink)
- TimeOracleFileLocker contract for blockchain-based time locking
- Secure file metadata storage on-chain
- Automated unlock mechanisms with time verification

### 4. Time Oracle Smart Rollup (Rust)
- Tezos smart rollup for decentralized time verification
- Consensus-based timestamp validation
- Quantum-resistant time oracle service
- Multi-source time validation for accuracy
- Rollup-based scalable time verification on Tezos

### 5. IPFS Storage Layer
- Decentralized file storage using IPFS
- Pinata service integration for reliable pinning
- Content addressing for immutable file references

## Security Features

### Post-Quantum Encryption
- *Kyber-768*: NIST-standardized post-quantum key encapsulation
- *AES-256-GCM*: Symmetric encryption for data protection
- *Hybrid Approach*: Combines classical and quantum-resistant cryptography

### Blockchain Security
- *Etherlink Integration*: Layer 2 scaling solution
- *Smart Contract Verification*: Immutable time locking logic
- *Decentralized Storage*: IPFS for censorship-resistant file storage

### Time Oracle Consensus
- *Multi-Source Verification*: Multiple timestamp sources for accuracy
- *Rollup-Based*: Scalable time verification on Tezos
- *Consensus Algorithm*: Ensures reliable time validation
- *Quantum-Resistant*: Future-proof time verification mechanisms

## Project Structure

```
timestone/
├── frontend/                 # Next.js React application
│   ├── src/
│   │   ├── app/             # App router pages
│   │   │   ├── landing/     # Landing page with 3D animations
│   │   │   ├── create/      # Time capsule creation
│   │   │   ├── dashboard/   # User dashboard
│   │   │   └── unlock/      # Capsule unlocking interface
│   │   ├── components/      # Reusable UI components
│   │   └── lib/            # Utility functions
│   └── package.json
├── backend/                  # Node.js Express server
│   ├── src/
│   │   ├── routes/          # API endpoints
│   │   │   ├── capsule.js   # Time capsule operations
│   │   │   ├── encryption.js # Kyber encryption/decryption
│   │   │   ├── ipfs.js      # IPFS file operations
│   │   │   ├── debug.js     # Debug endpoints
│   │   │   └── emergency.js # Emergency access
│   │   ├── services/        # Business logic
│   │   └── middleware/      # Express middleware
│   └── package.json
├── time-oracle-rollup/       # Tezos smart rollup
│   ├── src/
│   │   ├── lib.rs           # Main rollup implementation
│   ├── kernel.wasm          # Compiled rollup kernel
│   ├── Cargo.toml           # Rust dependencies
│   └── rollup_config.json   # Rollup configuration
├── Etherlink/               # Smart contracts
│   ├── contracts/
│   │   ├── TimeOracleFileLocker.sol  # Main contract
│   │   ├── TimeCapsule.sol           # Capsule management
│   │   └── TimeOracle.sol            # Oracle interface
│   ├── test/                # Contract tests
│   ├── scripts/             # Deployment scripts
│   └── hardhat.config.ts    # Hardhat configuration
└── README.md
```

## Complete User Flow

### 1. Capsule Creation Flow

User → Frontend → Backend → Smart Contract → IPFS
1. User uploads file/message via frontend
2. Frontend sends to backend encryption service
3. Backend generates Kyber key pair
4. File encrypted with hybrid encryption (Kyber + AES)
5. Encrypted file uploaded to IPFS
6. File metadata and IPFS hash stored on Etherlink contract
7. User receives private key for future decryption


### 2. Time Verification Flow (Time Oracle Rollup)

Smart Contract → Time Oracle Rollup → Consensus → Verification
1. User requests capsule unlock
2. Smart contract queries time oracle rollup
3. Rollup collects timestamps from multiple sources
4. Consensus algorithm validates current time
5. Rollup provides verified timestamp to contract
6. Contract validates unlock conditions
7. Access granted or denied based on time verification


### 3. Capsule Unlocking Flow

User → Frontend → Smart Contract → Backend → IPFS → Decryption
1. User provides private key and file ID
2. Frontend verifies unlock conditions via smart contract
3. Contract confirms time has passed via oracle rollup
4. Backend retrieves encrypted file from IPFS
5. File decrypted using Kyber private key
6. Original content returned to user


## Time Oracle Smart Rollup Details

### Architecture
The Time Oracle Smart Rollup is implemented in Rust and deployed on Tezos. It provides decentralized time verification services to the TimeStone platform.

### Core Components

#### Time Collection Module
- Collects timestamps from multiple authoritative sources
- NTP servers, blockchain timestamps, external APIs
- Validates source reliability and accuracy

#### Consensus Engine
- Implements Byzantine fault-tolerant consensus
- Handles conflicting timestamps from different sources
- Ensures majority agreement on current time

#### Verification Service
- Processes time verification requests from smart contracts
- Returns cryptographically signed timestamps
- Maintains audit trail of all time verifications

### Rollup Operations

#### Input Processing
rust
// Time verification request structure
struct TimeVerificationRequest {
    capsule_id: String,
    unlock_timestamp: u64,
    requester: Address,
}


#### Output Generation
rust
// Time verification response
struct TimeVerificationResponse {
    current_timestamp: u64,
    is_unlockable: bool,
    signature: Signature,
    sources_count: u32,
}


### Deployment Configuration

#### Rollup Parameters
- *Kernel*: Compiled WASM binary
- *Boot Sector*: Initial state configuration
- *Reveal Data*: External data access permissions
- *Origination Proof*: Deployment verification

#### Integration with Etherlink
- Cross-chain communication protocols
- Message passing between rollup and smart contracts
- State synchronization mechanisms

## Technology Stack

### Frontend
- *Next.js 15*: React framework with App Router
- *TypeScript*: Type-safe development
- *Tailwind CSS*: Utility-first styling
- *Framer Motion*: Smooth animations
- *Three.js*: 3D visual effects
- *RainbowKit + Wagmi*: Wallet integration
- *Ethers.js*: Ethereum interaction

### Backend
- *Node.js + Express*: RESTful API server
- *Kyber-768*: Post-quantum encryption
- *IPFS/Pinata*: Decentralized file storage
- *Multer*: File upload handling
- *Helmet*: Security middleware

### Blockchain
- *Etherlink*: Layer 2 scaling solution
- *Solidity*: Smart contract language
- *Hardhat*: Development framework
- *Tezos Smart Rollup*: Time oracle service

### Time Oracle Rollup
- *Rust*: Systems programming language
- *WASM*: WebAssembly compilation target
- *Tezos Protocol*: Rollup infrastructure
- *Cryptographic Libraries*: Signature and verification

### Infrastructure
- *IPFS*: Decentralized storage
- *Pinata*: IPFS pinning service
- *Web3.Storage*: Alternative IPFS gateway

## Getting Started

### Prerequisites
- Node.js 18+
- Rust (for rollup development)
- Hardhat (for smart contracts)
- IPFS node or Pinata account
- Tezos development tools

### Frontend Setup
```
cd frontend
npm install
npm run dev
```

### Backend Setup
```
cd backend
npm install
# Set environment variables
cp .env.example .env
npm run dev
```

### Smart Contract Setup
```
cd Etherlink
npm install
npx hardhat compile
npx hardhat test
npx hardhat deploy
```

### Time Oracle Rollup Setup
```
cd time-oracle-rollup
cargo build --target wasm32-unknown-unknown --release
# Deploy rollup to Tezos testnet
octez-smart-rollup-node-alpha run operator
```
### Deploy Tezos Smart Rollup (Time Oracle)

Step 1 – Become the tezos user
```
sudo adduser tezossudo -su tezos
```
Step 2 – Run Tezos L1 Node
```
octez-node run \  --data-dir /var/tezos/node \  --rpc-addr 127.0.0.1:8732
```
Wait until bootstrapped (may take 20–30 minutes).

Step 3 – Run Smart Rollup Node
```
octez-smart-rollup-node run \  --data-dir /var/tezos/smartrollup_sr1CWGm \  --rollup sr1CWmH7T4ujK34pkFebfKpVQFeaxjvwjR2
```
This uses the pre‑built rollup. To originate your own use: octez-smart-rollup-originator .... Tip: Visit the Tezos faucet and claim at least 12000 test tokens to cover rollup origination costs.

Step 4 – Folder Permissions Fix
```
sudo chmod -R 755 /home/user/timestone
sudo chown -R tezos:tezos /home/user/timestone/frontend/.next
sudo chown -R tezos:tezos /home/user/timestone/frontend/node_modules
```
Once running, integrate the rollup address into .env files as:

## Environment Variables

### Backend (.env)
```
PORT=3001
IPFS_NODE_URL=https://ipfs.infura.io:5001
WEB3_STORAGE_TOKEN=your_web3_storage_token
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000
TIME_ORACLE_ROLLUP_ADDRESS=your_rollup_address
TEZOS_RPC_URL=https://rpc.ghostnet.teztnets.xyz
TIME_ORACLE_ROLLUP_ADDRESS=sr1CWGmH7T4ujK34pkFebfKpVQFeaxjvwjR2
```

### Frontend (.env.local)
```
NEXT_PUBLIC_BACKEND_URL=http://localhost:3001
NEXT_PUBLIC_CONTRACT_ADDRESS=your_contract_address
NEXT_PUBLIC_CHAIN_ID=your_chain_id
NEXT_PUBLIC_ROLLUP_ADDRESS=your_rollup_address
```

### Time Oracle Rollup (.env)
```
TEZOS_NODE_URL=https://rpc.ghostnet.teztnets.xyz
ROLLUP_ADDRESS=your_rollup_address
OPERATOR_KEY=your_operator_private_key
DATA_DIR=./rollup_data
```

## API Endpoints

### Time Capsules
- POST /api/capsule/create - Create new time capsule
- GET /api/capsule/:id - Get capsule metadata
- POST /api/capsule/unlock - Unlock time capsule
- GET /api/capsule/stats - Get service statistics

### Encryption
- POST /api/encrypt/keypair - Generate Kyber key pair
- POST /api/encrypt/data - Encrypt data
- POST /api/encrypt/decrypt - Decrypt data
- POST /api/encrypt/validate - Validate key pair

### IPFS
- POST /api/pinata/upload - Upload file to IPFS
- GET /api/pinata/download/:cid - Download from IPFS
- DELETE /api/pinata/delete/:cid - Delete from IPFS

### Time Oracle
- POST /api/oracle/verify-time - Request time verification
- GET /api/oracle/status - Get rollup status
- GET /api/oracle/history/:capsule_id - Get verification history

## Security Considerations

### Quantum Resistance
- Kyber-768 provides protection against quantum attacks
- Hybrid encryption combines classical and post-quantum methods
- Regular key rotation recommended for long-term storage

### Smart Contract Security
- Time-based unlocking prevents premature access
- Multi-signature support for high-value capsules
- Emergency access mechanisms for critical situations

### Time Oracle Security
- Multi-source timestamp validation
- Byzantine fault tolerance
- Cryptographic proof of time verification
- Audit trail for all operations

### Data Privacy
- Files encrypted before IPFS storage
- Private keys never stored on servers
- Zero-knowledge time verification

## Use Cases

### Personal Time Capsules
- Birthday messages for future selves
- Graduation letters to children
- Anniversary surprises
- Legacy messages

### Business Applications
- Contract time locks
- Escrow services
- Document versioning
- Compliance requirements

### Creative Projects
- NFT time releases
- Art project reveals
- Music album drops
- Book chapter releases

## Future Enhancements

### Planned Features
- *Multi-chain Support*: Ethereum, Polygon, Arbitrum
- *Advanced Encryption*: Lattice-based cryptography
- *Social Features*: Shared time capsules
- *Mobile App*: iOS and Android applications
- *AI Integration*: Content analysis and categorization

### Scalability Improvements
- *Layer 2 Solutions*: Optimistic rollups
- *Sharding*: Horizontal scaling
- *CDN Integration*: Global content delivery
- *Caching*: Redis-based performance optimization

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- *NIST*: For post-quantum cryptography standards
- *Tezos Foundation*: For smart rollup technology
- *IPFS*: For decentralized storage
- *Etherlink*: For Layer 2 scaling solution

---

*TimeStone* - Where memories meet the future of cryptography.