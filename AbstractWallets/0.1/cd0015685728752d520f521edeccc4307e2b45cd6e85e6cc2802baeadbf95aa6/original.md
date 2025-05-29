```
send!(source::AbstractWallet, target, asset, quantity;
      fulfill_maximum=false, check, onfailure)
```

Send a certain amount of the given asset to a target if it is contained in this quantity in the original wallet. If `fulfill_maximum` is `true`, then fulfill as much of the transaction as possible.
