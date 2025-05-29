```
laguerre_id(a::Number, Nq, Ts)
```

Construct a discrete-time Laguerre basis of length `Nq` with poles at `-a` for system identification.

NOTE: for large `Nq`, this basis may be numerically ill-conditioned. Consider applying `balance_statespace` to the resulting basis.
