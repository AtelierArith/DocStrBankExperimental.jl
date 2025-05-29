```
GMGLinearSolver(
  mh::ModelHierarchy,
  trials::FESpaceHierarchy,
  tests::FESpaceHierarchy,
  biforms::AbstractArray{<:Function},
  interp,
  restrict;
  pre_smoothers   = Fill(RichardsonSmoother(JacobiLinearSolver(),10),num_levels(mh)-1),
  post_smoothers  = pre_smoothers,
  coarsest_solver = Gridap.Algebra.LUSolver(),
  mode::Symbol    = :preconditioner,
  is_nonlinear    = false,
  maxiter = 100, atol = 1.0e-14, rtol = 1.0e-08, verbose = false,
)
```

Creates an instance of [`GMGLinearSolverFromMatrices`](@ref) from the underlying model  hierarchy, the trial and test FEspace hierarchies, the weakform lhs at each level  and the transfer operators and smoothers at each level except the coarsest.

The solver has two modes of operation, defined by the kwarg `mode`:

  * `:solver`: The GMG solver takes a rhs `b` and returns a solution `x`.
  * `:preconditioner`: The GMG solver takes a residual `r` and returns a correction `dx`.
