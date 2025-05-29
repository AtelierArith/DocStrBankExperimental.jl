```
ai!(rop, x, rnd)
```

Set `rop` to the value of the Airy function Ai on `x`, rounded in the direction `rnd`.  When `x` is NaN, `rop` is always set to NaN. When `x` is +Inf or −Inf, `rop` is +0. The current implementation is not intended to be used with large arguments. It works with `|x|` typically smaller than 500.
