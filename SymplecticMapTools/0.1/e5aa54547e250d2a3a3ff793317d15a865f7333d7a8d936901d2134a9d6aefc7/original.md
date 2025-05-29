```
vector_mpe_backslash(x::AbstractArray, K::Integer)
```

Applies Birkhoff vector MPE to a sequence `x_n = x[:, n]` using the LSQR algorithm. This currently does not have preconditioning, and therefore is less accurate than `vector_mpe_backslash`.

Arguments:

  * `x`: The sequence
  * `K`: The number of unknowns in the filter
  * `c0`: The initial guess of
  * `atol`, `btol`: Tolerances. See `IterativeSolvers.lsqr!`
