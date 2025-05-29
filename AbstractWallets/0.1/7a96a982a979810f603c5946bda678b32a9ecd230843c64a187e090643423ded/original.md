```
quantity_contained(wallet::AbstractWallet{K}, asset::K)
```

Calculate the amount of `asset` contained in the `wallet`. If the asset is not in the wallet, a suitable null value should be returned.
