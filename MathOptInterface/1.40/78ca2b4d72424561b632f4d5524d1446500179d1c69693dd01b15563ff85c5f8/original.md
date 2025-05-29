```
DUAL_INFEASIBLE::TerminationStatusCode
```

An instance of the [`TerminationStatusCode`](@ref) enum.

## About

The algorithm proved that no dual feasible solution exists.

To check if the primal problem is feasible, set the objective sense to [`FEASIBILITY_SENSE`](@ref) and re-solve the problem.

If a primal feasible point does not exist, the original problem is both primal and dual infeasible.

If a primal feasible solution exists, this status typically implies that the problem is unbounded, with some technical exceptions (for example, if the problem is a conic optimization problem in which strong duality does not hold).

The technical exceptions do not apply to linear programs. The combination of [`DUAL_INFEASIBLE`](@ref) and a primal feasible point means that the primal linear program is unbounded.
