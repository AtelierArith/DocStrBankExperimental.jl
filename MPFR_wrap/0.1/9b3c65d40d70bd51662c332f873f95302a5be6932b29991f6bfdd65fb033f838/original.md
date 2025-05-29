```
y0!(rop, op, rnd)
```

Set `rop` to the value of the second kind Bessel function of order 0 on `op`, rounded in the direction `rnd`. When `op` is NaN or negative, `rop` is always set to NaN. When `op` is +Inf, `rop` is set to +0. When `op` is zero, `rop` is set to -Inf.
