```
destroy!(wallet::AbstractWallet, asset, quantity;
         fulfill_maximum=false, check, onfailure)
```

Destroy a certain amount of the given asset if it is contained in the wallet. If `fulfill_maximum` is `true`, then fulfill as much of the transaction as possible.
