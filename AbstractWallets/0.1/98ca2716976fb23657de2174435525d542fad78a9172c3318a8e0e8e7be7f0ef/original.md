```
build_send_transaction(source::AbstractWallet, target, asset, quantity;
                       fulfill_maximum=false)
```

Prepare transaction which will send a certain amount of the given `asset` to the `target` if it is contained in this `quantity` in the original `wallet`. If `fulfill_maximum` is `true`, then fulfill as much of the transaction as possible.
