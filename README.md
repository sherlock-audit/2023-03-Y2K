
# Y2K Finance contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Resources

- [[Notion page with flowchart and videos]]([url](https://y2kfinance.notion.site/Earthquake-V2-Documentation-9766c278d4a14c619ba92017a69853e4))
- [[V1 Docs]](https://y2k-finance.gitbook.io/y2k-finance/products/earthquake/contracts-and-audits)

# On-chain context

```
DEPLOYMENT: [Arbitrum]
ERC20: [WETH, USDC]
ERC1155: [Earthquake VaultV2]
FEE-ON-TRANSFER: [none]
REBASING TOKENS: [none]
ADMIN: [restricted]  
EXTERNAL-ADMINS: [trusted]
```


Please answer the following questions to provide more context: 
### Q: Are there any additional protocol roles? If yes, please explain in detail:
1) Admin, Timelocker. Admin is EOA assinged on deployment, Timelock is a contract with Msig as owner. 
2) Admin can configure new markets and epochs on those markets, Timelock can make cirital changes like changing the oracle or whitelisitng controllers.
3) For convinience the Admin is able to whitelist the first controller, Also the admin is configuring the oracle, however oracles are public and will be linked on mint page on the Front end. 
4) No rugging 

A: 

___
### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
A: Should comply wiht 1155 standart

___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
A: Admin is seting oracles when configuring new markets, users have the ability to investigate the oracle before mint. Admin is able to whitelist controller once for convenience to include setting controller in deployment script. Admin configuring markets or epochs, so this can be done programmatically 

____
### Q: Please provide links to previous audits (if any).
A: https://y2k-finance.gitbook.io/y2k-finance/products/earthquake/contracts-and-audits/audits

___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)? 
A: Settlement of vaults is permissionless, however on epoch configuratoin Gelato Network as well as Chainlink keeper is deployed. 
_____

### Q: In case of external protocol integrations, are the risks of an external protocol pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality. 
A: [NOT ACCEPTABLE] 


# Audit scope


[Earthquake @ 736b2e1e51bef6daa6a5ecd1decb7d156316d795](https://github.com/Y2K-Finance/Earthquake/tree/736b2e1e51bef6daa6a5ecd1decb7d156316d795)
- [Earthquake/src/v2/Carousel/Carousel.sol](Earthquake/src/v2/Carousel/Carousel.sol)
- [Earthquake/src/v2/Carousel/CarouselFactory.sol](Earthquake/src/v2/Carousel/CarouselFactory.sol)
- [Earthquake/src/v2/Controllers/ControllerPeggedAssetV2.sol](Earthquake/src/v2/Controllers/ControllerPeggedAssetV2.sol)
- [Earthquake/src/v2/SemiFungibleVault.sol](Earthquake/src/v2/SemiFungibleVault.sol)
- [Earthquake/src/v2/TimeLock.sol](Earthquake/src/v2/TimeLock.sol)
- [Earthquake/src/v2/VaultFactoryV2.sol](Earthquake/src/v2/VaultFactoryV2.sol)
- [Earthquake/src/v2/VaultV2.sol](Earthquake/src/v2/VaultV2.sol)
- [Earthquake/src/v2/interfaces/ICarousel.sol](Earthquake/src/v2/interfaces/ICarousel.sol)
- [Earthquake/src/v2/interfaces/ISemiFungibleVault.sol](Earthquake/src/v2/interfaces/ISemiFungibleVault.sol)
- [Earthquake/src/v2/interfaces/IVaultFactoryV2.sol](Earthquake/src/v2/interfaces/IVaultFactoryV2.sol)
- [Earthquake/src/v2/interfaces/IVaultV2.sol](Earthquake/src/v2/interfaces/IVaultV2.sol)
- [Earthquake/src/v2/interfaces/IWETH.sol](Earthquake/src/v2/interfaces/IWETH.sol)
- [Earthquake/src/v2/libraries/CarouselCreator.sol](Earthquake/src/v2/libraries/CarouselCreator.sol)
- [Earthquake/src/v2/libraries/VaultV2Creator.sol](Earthquake/src/v2/libraries/VaultV2Creator.sol)



# About [Y2K Finance]

Y2K Finance is a suite of structured products designed for exotic peg derivatives, that will allow market participants the ability to robustly hedge or speculate on the risk of a particular pegged asset (or basket of pegged assets), deviating from their ‘fair implied market value’.
