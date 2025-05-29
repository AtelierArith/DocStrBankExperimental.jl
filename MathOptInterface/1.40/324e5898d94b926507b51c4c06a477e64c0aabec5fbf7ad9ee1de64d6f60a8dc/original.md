```
LOCALLY_INFEASIBLE::TerminationStatusCode
```

An instance of the [`TerminationStatusCode`](@ref) enum.

## About

The algorithm converged to an infeasible point or otherwise completed its search without finding a feasible solution, without guarantees that no feasible solution exists.

If you know a primal feasible solution exists, use [`VariablePrimalStart`](@ref) to provide a feasible starting point to the solver.
