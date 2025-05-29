```
jn!(rop, n, op, rnd)
```

Set `rop` to the value of the first kind Bessel function of order `n` on `op`, rounded in the direction `rnd`. When `op` is NaN, `rop` is always set to NaN. When `op` is ±Inf, `rop` is set to +0. When `op` is zero, and `n` is not zero, `rop` is set to +0 or −0 depending on the parity and sign of `n`, and the sign of `op`.
