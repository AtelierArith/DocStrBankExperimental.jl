```
r = rtf(z, p, k; Ts = rts, var = rvar)
```

Create from the roots (zeros) `z`, poles `p`, gain `k`, sampling time `rts` and variable name `rvar` the rational transfer function `r(λ) = k*num(λ)/den(λ)`, where `num(λ)` and `den(λ)` are monic polynomials with roots equal `z` and `p`, respectively, and such that `r.Ts = rts` (default `rts = 0`)  and `r.var = rvar` (default `rvar = :s` if `Ts = 0` or `rvar = :z` if `Ts ≠ 0`). 
