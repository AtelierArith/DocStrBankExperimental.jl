```
log2!(rop, op, rnd)
```

Set `rop` to log₂ of `op` rounded in the direction `rnd`. Set `rop` to +0 if `op` is 1 (in all rounding modes), for consistency with the ISOC99 and IEEE 754-2008 standards. Set `rop` to −Inf if `op` is ±0 (i.e., the sign of the zero has no influence on the result).
