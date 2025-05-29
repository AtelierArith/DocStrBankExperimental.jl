```
lin_solve(solver::LinSolver, b::AbstractVecOrMat; tol=0)
```

This function solves the linear system represented in `solver::LinSolver` with a right-hand side `b`. The `tol` kwarg is controlling how accurate the linear system needs to be solved. A NEP-algorithm will call this solver every time a linear system associated with `M(λ)` needs to be solved.

This function must be overloaded if a user wants to define their own way of solving linear systems. See [`LinSolver`](@ref) for examples.
