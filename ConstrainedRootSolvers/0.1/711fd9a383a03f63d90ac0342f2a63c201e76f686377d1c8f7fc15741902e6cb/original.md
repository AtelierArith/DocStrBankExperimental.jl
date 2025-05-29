Tolerance for target function residual

```julia
struct ResidualTolerance{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# Fields

  * `tol::Any`: Tolerance for residual
  * `n_limit::Int64`: limit of iterations
