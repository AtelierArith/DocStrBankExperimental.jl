```
yn!(rop, n, op, rnd)
```

Set `rop` to the value of the second kind Bessel function of order `n` on `op`, rounded in the direction `rnd`. When `op` is NaN or negative, `rop` is always set to NaN. When `op` is +Inf, `rop` is set to +0. When `op` is zero, `rop` is set to +Inf or −Inf depending on the parity and sign of `n`.
