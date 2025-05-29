```
build_destroy_transaction(wallet::AbstractWallet, asset, quantity;
                          fulfill_maximum=false)
```

Prepare transaction which will destroy a certain amount of the given `asset` if it is contained in this `quantity` in the original `wallet`. If `fulfill_maximum` is `true`, then fulfill as much of the transaction as possible.
