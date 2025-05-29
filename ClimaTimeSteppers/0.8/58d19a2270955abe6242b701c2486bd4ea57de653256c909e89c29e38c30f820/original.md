```
ConstantForcing(rtol)
```

A `ForcingTerm` that always returns the value `rtol`, which must be in the interval `[0, 1)`. If `x` and `f!` satisfy certain assumptions, this forcing term guarantees that the Newton-Krylov method will converge linearly with an asymptotic rate of at most `rtol`. If `rtol` is 0 (or `eps(FT)`), this forces the approximation of `Δx[n]` to be exact (or exact to within machine precision) and guarantees that the Newton-Krylov method will converge quadratically. Note that, although a smaller value of `rtol` guarantees faster asymptotic convergence, it also leads to a higher probability of oversolving.
