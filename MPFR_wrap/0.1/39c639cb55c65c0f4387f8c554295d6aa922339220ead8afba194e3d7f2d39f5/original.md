```
modf!(iop, fop, op, rnd)
```

Set simultaneously `iop` to the integral part of `op` and `fop` to the fractional part of `op`, rounded in the direction `rnd` with the corresponding precision of `iop` and `fop` (equivalent to `trunc!(iop, op, rnd)` and `frac(fop, op, rnd)`). The variables `iop` and `fop` must be different.
