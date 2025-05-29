```
reduced_residual(
  solver::RBSolver,
  op::ParamOperator,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> AffineContribution
```

Reduces the residual contained in `op` via hyper-reduction. This function first builds the residual snapshots, which are then reduced according to the strategy `residual_reduction` specified in the reduced solver `solver`
