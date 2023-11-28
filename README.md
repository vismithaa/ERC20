# ERC20 Contract

In the solidity code , I have used ERC20 token contract libraries from openzeppelin to interact and deploy.

## Description

* Contract Definition:

contract Wow is ERC20, ERC20Burnable, Ownable, ERC20Permit { ... }: Defines a new contract named Wow that inherits from ERC20, ERC20Burnable, Ownable, and ERC20Permit. This means that the Wow contract includes the functionalities provided by these inherited contracts.
* Constructor:

constructor(address initialOwner) ERC20("wow", "W") Ownable(initialOwner) ERC20Permit("wow") { ... }: The constructor is executed once when the contract is deployed. It initializes the contract with a name ("wow"), symbol ("W"), and mints an initial supply of 1 token to the deployer (the person who deploys the contract).
* Custom Function:

function mint(address to, uint256 amount) public onlyOwner { ... }: Allows the owner (address set during deployment) to mint additional tokens and send them to a specified address. This function is only callable by the owner due to the onlyOwner modifier.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ERC20.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts@5.0.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@5.0.0/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts@5.0.0/access/Ownable.sol";
import "@openzeppelin/contracts@5.0.0/token/ERC20/extensions/ERC20Permit.sol";

contract Wow is ERC20, ERC20Burnable, Ownable, ERC20Permit {
    constructor(address initialOwner)
        ERC20("wow", "W")
        Ownable(initialOwner)
        ERC20Permit("wow")
    {
        _mint(msg.sender, 1 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }

    // function burn(uint256 amount)public override  {
    //  _burn(msg.sender,amount);
    // }
    // function tranfer(address to,uint256 amount)public override  {
    //  _transfer(msg.sender,to,amount);
    // }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.20" (or another compatible version), and then click on the "Compile ERC20.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "ERC20" contract from the dropdown menu, and then click on the "Deploy" button.

Make sure you pass the owner's address while deploying .


## Authors

Vismitha P
@vismithaaap@gmail.com

## License

This project is licensed under the MIT License - see the LICENSE.md file for details
