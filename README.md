Lottery Smart Contract

Overview

This is a decentralized lottery smart contract written in Solidity. Participants can enter the lottery by sending at least 1 Ether to the contract. The contract randomly selects a winner once there are at least three participants and transfers the total balance to the winner.

Features

1.Manager Privileges: Only the contract deployer (manager) can view the balance and select the winner.

2.Secure Participation: Participants must send at least 1 Ether to join.

3.Random Winner Selection: Uses keccak256 hashing to generate a random winner.

4.Automatic Fund Transfer: The winner receives the total contract balance.

Requirements

Solidity version 0.5.0 - 0.9.0

Ethereum development environment (Remix, Hardhat, Truffle, etc.)

A wallet with sufficient Ether for deploying and testing (e.g., MetaMask)

How It Works

Deployment: The manager deploys the contract.

Joining the Lottery: Participants send at least 1 Ether to enter.

Random Number Generation: Uses keccak256 with block data to generate randomness.

Winner Selection: The manager triggers the selectWinner function, selecting a random participant and transferring the balance.
Contract Functions

receive() external payable

Allows users to enter the lottery by sending at least 1 Ether.

Adds the sender to the participants array.

getBalance() public view returns (uint)

Returns the total balance of the contract.

Can only be called by the manager.

random() public view returns (uint)

Generates a pseudo-random number using keccak256.

Uses block properties and the number of participants.

selectWinner() public

Can only be executed by the manager.

Requires at least three participants.

Randomly selects a winner and transfers the contract balance.

Security Considerations

Pseudo-Randomness: The contract relies on keccak256, which is predictable. For better randomness, use Chainlink VRF.

Reentrancy Protection: The contract directly transfers funds; consider using call with a checks-effects-interactions pattern.

License

This project is licensed under the GPL-3.0 License.

