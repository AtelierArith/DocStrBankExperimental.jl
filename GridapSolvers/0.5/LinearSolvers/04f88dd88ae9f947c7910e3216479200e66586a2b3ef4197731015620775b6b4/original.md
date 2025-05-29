```
GMGLinearSolver(
  mh::ModelHierarchy,
  matrices::AbstractArray{<:AbstractMatrix},
  prolongations,
  restrictions;
  pre_smoothers   = Fill(RichardsonSmoother(JacobiLinearSolver(),10),num_levels(mh)-1),
  post_smoothers  = pre_smoothers,
  coarsest_solver = LUSolver(),
  mode::Symbol    = :preconditioner,
  maxiter = 100, atol = 1.0e-14, rtol = 1.0e-08, verbose = false,
)
```

Creates an instance of [`GMGLinearSolverFromMatrices`](@ref) from the underlying model  hierarchy, the system matrices at each level and the transfer operators and smoothers  at each level except the coarsest.

The solver has two modes of operation, defined by the kwarg `mode`:

  * `:solver`: The GMG solver takes a rhs `b` and returns a solution `x`.
  * `:preconditioner`: The GMG solver takes a residual `r` and returns a correction `dx`.
