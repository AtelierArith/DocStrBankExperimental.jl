```
`status(:: AbstractStopping; list = false)`
```

Returns the status of the algorithm:

The different statuses are:

  * `Optimal`: reached an optimal solution.
  * `SubProblemFailure`
  * `SubOptimal`: reached an acceptable solution.
  * `Unbounded`: current iterate too large in norm.
  * `UnboundedPb`: unbouned problem.
  * `Stalled`: stalled algorithm.
  * `IterationLimit`: too many iterations of the algorithm.
  * `TimeLimit`: time limit.
  * `EvaluationLimit`: too many ressources used,                         i.e. too many functions evaluations.
  * `ResourcesOfMainProblemExhausted`: in the case of a substopping, EvaluationLimit or TimeLimit for the main stopping.
  * `Infeasible`: default return value, if nothing is done the problem is              considered feasible.
  * `StopByUser`: stopped by the user.
  * `DomainError`: there is a NaN somewhere.
  * `Exception`: unhandled exception
  * `Unknwon`: if stopped for reasons unknown by Stopping.

Note:

  * Set keyword argument `list` to true, to get an `Array` with all the statuses.
  * The different statuses correspond to boolean values in the meta.
