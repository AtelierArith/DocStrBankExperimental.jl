Tolerance for 2D and above solution

```julia
struct SolutionToleranceND{FT} <: ConstrainedRootSolvers.AbstractTolerance{FT}
```

# Fields

  * `tol::Vector`: Tolerance for solution
  * `n_limit::Int64`: limit of iterations
