Tolerance for solution

```julia
struct SolutionTolerance{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# Fields

  * `tol::Any`: Tolerance for solution
  * `n_limit::Int64`: limit of iterations
