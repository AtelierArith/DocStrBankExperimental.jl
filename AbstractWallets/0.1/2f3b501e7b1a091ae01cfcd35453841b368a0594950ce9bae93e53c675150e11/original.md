```
quantity_contained(portfolio::AbstractPortfolio{K}, asset::K)
```

Calculate the amount of `asset` contained in the `portfolio`. If the asset is not in the wallet, a suitable null value should be returned.
