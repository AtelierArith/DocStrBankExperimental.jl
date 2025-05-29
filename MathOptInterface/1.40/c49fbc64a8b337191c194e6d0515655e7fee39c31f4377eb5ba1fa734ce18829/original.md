```
INFEASIBLE_OR_UNBOUNDED::TerminationStatusCode
```

An instance of the [`TerminationStatusCode`](@ref) enum.

## About

The algorithm stopped because it proved that the problem is infeasible or unbounded, without distinguishing between the two cases.

To distinguish between the two cases, set the objective sense to [`FEASIBILITY_SENSE`](@ref) and re-solve the problem. If a primal feasible point exists, the original problem is unbounded. If a primal feasible point does not exist, the original problem is infeasible.
