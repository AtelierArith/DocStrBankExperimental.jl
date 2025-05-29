```
reduced_jacobian(
  solver::RBSolver,
  op::ParamOperator,
  red_trial::RBSpace,
  red_test::RBSpace,
  s::AbstractSnapshots
  ) -> Union{AffineContribution,TupOfAffineContribution}
```

Reduces the Jacobian contained in `op` via hyper-reduction. This function first builds the Jacobian snapshots, which are then reduced according to the strategy `reduced_jacobian` specified in the reduced solver `solver`. In transient applications, the output is a tuple of length equal to the number of Jacobians(i.e., equal to the order of the ODE plus one)
