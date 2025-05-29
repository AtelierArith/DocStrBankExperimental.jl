```
eval_performance(
  solver::RBSolver,
  feop::ParamOperator,
  fesnaps::AbstractSnapshots,
  rbsnaps::AbstractSnapshots,
  festats::CostTracker,
  rbstats::CostTracker
  ) -> ROMPerformance
```

Arguments:

  * `solver`: solver for the reduced problem
  * `feop`: FE operator representing the PDE
  * `fesnaps`: online snapshots of the FE solution
  * `rbsnaps`: reduced approximation of `fesnaps`
  * `festats`: time and memory consumption needed to compute `fesnaps`
  * `rbstats`: time and memory consumption needed to compute `rbsnaps`

Returns the performance of the reduced algorithm, in terms of the (relative) error between `rbsnaps` and `fesnaps`, and the computational speedup between `rbstats` and `festats`
