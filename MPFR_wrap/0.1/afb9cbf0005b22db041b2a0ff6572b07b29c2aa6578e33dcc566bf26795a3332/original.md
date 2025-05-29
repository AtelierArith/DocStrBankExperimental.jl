```
j1!(rop, op, rnd)
```

Set `rop` to the value of the first kind Bessel function of order 1 on `op`, rounded in the direction `rnd`. When `op` is NaN, `rop` is always set to NaN. When `op` is ±Inf, `rop` is set to +0. When `op` is zero, `rop` is set to +0 or −0 depending on the sign of `op`.
