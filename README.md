# SportsToken Smart Contract

## Overview

The `SportsToken` smart contract is an ERC20 token with additional functionalities for managing sports equipment as redeemable assets. The contract allows users to mint, burn, transfer tokens, and redeem sports equipment using these tokens. Additionally, the contract owner can modify the inventory of sports equipment.

## Features

1. **Minting Tokens:** The owner can mint new tokens.
2. **Burning Tokens:** Users can burn their tokens.
3. **Transferring Tokens:** Users can transfer tokens to other addresses.
4. **Redeeming Sports Equipment:** Users can redeem sports equipment by burning tokens.
5. **Managing Inventory:** The owner can modify the inventory of sports equipment.

## Contract Details

### Inheritance
- `ERC20`: Implements the ERC20 token standard.
- `Ownable`: Provides basic authorization control.
- `ERC20Burnable`: Adds burnable token functionality.

### Events
- `LogMessage(string message)`: Emits messages for various actions like burning tokens and redeeming equipment.

### Structures
- `SportsEquipment`: Struct to store product details including name, cost, and inventory.

### Mappings
- `sportsEquipments`: Maps equipment type to its details.
- `redeemedProducts`: Maps user addresses to a list of redeemed products.
- `userTokenBalances`: Maps user addresses to their token balances.

### Constructor
Initializes the contract with predefined sports equipment and their respective details (product name, cost, inventory).

### Functions

- **mint(address recipientAddress, uint256 tokenAmount):**
  Mints `tokenAmount` tokens to `recipientAddress`. Only the contract owner can call this function.

- **burn_(uint256 tokenAmount):**
  Burns `tokenAmount` tokens from the caller's balance.

- **transfer_(address recipientAddress, uint256 tokenAmount):**
  Transfers `tokenAmount` tokens from the caller to `recipientAddress`.

- **redeemSportsEquipment(string memory equipmentType, uint256 quantity):**
  Redeems `quantity` of `equipmentType` by burning the necessary amount of tokens. Updates the inventory and records the redeemed products for the user.

- **MyRedeemedProducts(address recipient):**
  Returns the list of products redeemed by `recipient`.

- **modifyEquipmentQuantity(string memory equipmentType, uint256 newQuantity):**
  Modifies the inventory of `equipmentType` to `newQuantity`. Only the contract owner can call this function.

## Usage

### Deployment
Deploy the contract to an Ethereum network using a development framework like Hardhat or Truffle.

### Interacting with the Contract

#### Minting Tokens
To mint tokens, call the `mint` function with the recipient's address and the amount of tokens to be minted.

```solidity
mint(recipientAddress, tokenAmount);
```

#### Burning Tokens
To burn tokens, call the `burn_` function with the amount of tokens to be burned.

```solidity
burn_(tokenAmount);
```

#### Transferring Tokens
To transfer tokens, call the `transfer_` function with the recipient's address and the amount of tokens to be transferred.

```solidity
transfer_(recipientAddress, tokenAmount);
```

#### Redeeming Sports Equipment
To redeem sports equipment, call the `redeemSportsEquipment` function with the type of equipment and the quantity.

```solidity
redeemSportsEquipment("Ball", 2);
```

#### Viewing Redeemed Products
To view the list of products redeemed by a user, call the `MyRedeemedProducts` function with the user's address.

```solidity
MyRedeemedProducts(userAddress);

## License
This project is licensed under the MIT License.
