```
step!(
    cache::AbstractNonlinearSolveCache;
    recompute_jacobian::Union{Nothing, Bool} = nothing
)
```

Performs one step of the nonlinear solver.

### Keyword Arguments

  * `recompute_jacobian`: allows controlling whether the jacobian is recomputed at the current step. If `nothing`, then the algorithm determines whether to recompute the jacobian. If `true` or `false`, then the jacobian is recomputed or not recomputed, respectively. For algorithms that don't use jacobian information, this keyword is ignored with a one-time warning.
