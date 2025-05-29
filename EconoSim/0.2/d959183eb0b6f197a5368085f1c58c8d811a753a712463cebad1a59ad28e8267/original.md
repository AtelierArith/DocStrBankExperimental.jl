```
transfer_dem_free!(source::Balance, destination::Balance, amount::Real)
```

Transfer a part or all of the demurrage free buffer from one balance to another. No more than the available demurrage free buffer can be transferred.

  * source::Balance - the balance from which the demurrage free amount is taken.
  * destination::Balance - the balance to which the demurrage free buffer is transferred.
  * amount::Real - the amount to be transferred.
  * return - whether or not the transaction was succesful.
