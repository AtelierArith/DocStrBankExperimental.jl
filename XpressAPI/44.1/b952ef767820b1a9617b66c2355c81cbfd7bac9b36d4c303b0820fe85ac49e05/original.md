```
XPRS_SERIALIZEPREINTSOL
```

Setting `SERIALIZEPREINTSOL` to 1 will ensure that the `preintsol` callback is always fired in a deterministic order during a parallel MIP solve. (integer)

This applies only when the control DETERMINISTIC is set to `1`.

Default value: `0`

Values: 0 : The `preintsol` callbacks will be fired asynchronously from different threads. 1 : The `preintsol` callbacks will be fired in a deterministic order.
