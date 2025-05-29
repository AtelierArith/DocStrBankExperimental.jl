```
Xc = plyap(sys::AbstractStateSpace, Ql; kwargs...)
```

Lyapunov solver that takes the `L` Cholesky factor of `Q` and returns a triangular matrix `Xc` such that `Xc*Xc' = X`.
