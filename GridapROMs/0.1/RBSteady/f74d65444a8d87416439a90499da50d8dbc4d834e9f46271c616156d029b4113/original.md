```
reduced_weak_form(
  solver::RBSolver,
  op::ParamOperator,
  red_trial::RBSpace,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> (AffineContribution,Union{AffineContribution,TupOfAffineContribution})
```

Reduces the residual/Jacobian contained in `op` via hyper-reduction. Check the functions [`reduced_residual`](@ref) and [`reduced_jacobian`](@ref) for more details
