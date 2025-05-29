```
TerminationStatusCode
```

An Enum of possible values for the `TerminationStatus` attribute. This attribute is meant to explain the reason why the optimizer stopped executing in the most recent call to [`optimize!`](@ref).

If no call has been made to [`optimize!`](@ref), then the `TerminationStatus` is:

  * `OPTIMIZE_NOT_CALLED`: The algorithm has not started.

## OK

These are generally OK statuses, i.e., the algorithm ran to completion normally.

  * `OPTIMAL`: The algorithm found a globally optimal solution.
  * `INFEASIBLE`: The algorithm concluded that no feasible solution exists.
  * `DUAL_INFEASIBLE`: The algorithm concluded that no dual bound exists for the problem. If, additionally, a feasible (primal) solution is known to exist, this status typically implies that the problem is unbounded, with some technical exceptions.
  * `LOCALLY_SOLVED`: The algorithm converged to a stationary point, local optimal solution, could not find directions for improvement, or otherwise completed its search without global guarantees.
  * `LOCALLY_INFEASIBLE`: The algorithm converged to an infeasible point or otherwise completed its search without finding a feasible solution, without guarantees that no feasible solution exists.
  * `INFEASIBLE_OR_UNBOUNDED`: The algorithm stopped because it decided that the problem is infeasible or unbounded; this occasionally happens during MIP presolve.

## Solved to relaxed tolerances

  * `ALMOST_OPTIMAL`: The algorithm found a globally optimal solution to relaxed tolerances.
  * `ALMOST_INFEASIBLE`: The algorithm concluded that no feasible solution exists within relaxed tolerances.
  * `ALMOST_DUAL_INFEASIBLE`: The algorithm concluded that no dual bound exists for the problem within relaxed tolerances.
  * `ALMOST_LOCALLY_SOLVED`: The algorithm converged to a stationary point, local optimal solution, or could not find directions for improvement within relaxed tolerances.

## Limits

The optimizer stopped because of some user-defined limit.

  * `ITERATION_LIMIT`: An iterative algorithm stopped after conducting the maximum number of iterations.
  * `TIME_LIMIT`: The algorithm stopped after a user-specified computation time.
  * `NODE_LIMIT`: A branch-and-bound algorithm stopped because it explored a maximum number of nodes in the branch-and-bound tree.
  * `SOLUTION_LIMIT`: The algorithm stopped because it found the required number of solutions. This is often used in MIPs to get the solver to return the first feasible solution it encounters.
  * `MEMORY_LIMIT`: The algorithm stopped because it ran out of memory.
  * `OBJECTIVE_LIMIT`: The algorithm stopped because it found a solution better than a minimum limit set by the user.
  * `NORM_LIMIT`: The algorithm stopped because the norm of an iterate became too large.
  * `OTHER_LIMIT`: The algorithm stopped due to a limit not covered by one of the above.

## Problematic

This group of statuses means that something unexpected or problematic happened.

  * `SLOW_PROGRESS`: The algorithm stopped because it was unable to continue making progress towards the solution.
  * `NUMERICAL_ERROR`: The algorithm stopped because it encountered unrecoverable numerical error.
  * `INVALID_MODEL`: The algorithm stopped because the model is invalid.
  * `INVALID_OPTION`: The algorithm stopped because it was provided an invalid option.
  * `INTERRUPTED`: The algorithm stopped because of an interrupt signal.
  * `OTHER_ERROR`: The algorithm stopped because of an error not covered by one of the statuses defined above.
