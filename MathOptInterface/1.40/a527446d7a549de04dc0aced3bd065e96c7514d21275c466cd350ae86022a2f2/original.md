```
TerminationStatusCode
```

An Enum of possible values for the [`TerminationStatus`](@ref) attribute.

This attribute explains why the optimizer stopped executing in the most recent call to [`optimize!`](@ref).

## Values

### [`OPTIMIZE_NOT_CALLED`](@ref)

The algorithm has not started.

### [`OPTIMAL`](@ref)

The algorithm found a globally optimal solution.

### [`INFEASIBLE`](@ref)

The algorithm proved that no primal feasible solution exists.

### [`DUAL_INFEASIBLE`](@ref)

The algorithm proved that no dual feasible solution exists.

To check if the primal problem is feasible, set the objective sense to    [`FEASIBILITY_SENSE`](@ref) and re-solve the problem.

If a primal feasible point does not exist, the original problem is both    primal and dual infeasible.

If a primal feasible solution exists, this status typically implies that the    problem is unbounded, with some technical exceptions (for example, if the    problem is a conic optimization problem in which strong duality does not    hold).

The technical exceptions do not apply to linear programs. The combination of    [`DUAL_INFEASIBLE`](@ref) and a primal feasible point means that the primal    linear program is unbounded.

### [`LOCALLY_SOLVED`](@ref)

The algorithm converged to a stationary point, local optimal solution, could    not find directions for improvement, or otherwise completed its search    without global guarantees.

### [`LOCALLY_INFEASIBLE`](@ref)

The algorithm converged to an infeasible point or otherwise completed its    search without finding a feasible solution, without guarantees that no    feasible solution exists.

If you know a primal feasible solution exists, use    [`VariablePrimalStart`](@ref) to provide a feasible starting point to the    solver.

### [`INFEASIBLE_OR_UNBOUNDED`](@ref)

The algorithm stopped because it proved that the problem is infeasible or    unbounded, without distinguishing between the two cases.

To distinguish between the two cases, set the objective sense to    [`FEASIBILITY_SENSE`](@ref) and re-solve the problem. If a primal feasible    point exists, the original problem is unbounded. If a primal feasible point    does not exist, the original problem is infeasible.

### [`ALMOST_OPTIMAL`](@ref)

The algorithm found a globally optimal solution to relaxed tolerances.

### [`ALMOST_INFEASIBLE`](@ref)

The algorithm concluded that no feasible solution exists within relaxed    tolerances.

### [`ALMOST_DUAL_INFEASIBLE`](@ref)

The algorithm concluded that no dual bound exists for the problem within    relaxed tolerances.

### [`ALMOST_LOCALLY_SOLVED`](@ref)

The algorithm converged to a stationary point, local optimal solution, or    could not find directions for improvement within relaxed tolerances.

### [`ITERATION_LIMIT`](@ref)

An iterative algorithm stopped after conducting the maximum number of    iterations.

### [`TIME_LIMIT`](@ref)

The algorithm stopped after a user-specified computation time.

This status may be returned in relation to the [`TimeLimitSec`](@ref)    attribute, or some other solver-specific attribute.

### [`NODE_LIMIT`](@ref)

A branch-and-bound algorithm stopped because it explored a maximum number of    nodes in the branch-and-bound tree.

This status may be returned in relation to the [`NodeLimit`](@ref)    attribute, or some other solver-specific attribute.

### [`SOLUTION_LIMIT`](@ref)

The algorithm stopped because it found the required number of solutions.    This is often used in MIPs to get the solver to return the first feasible    solution it encounters.

This status may be returned in relation to the [`SolutionLimit`](@ref)    attribute, or some other solver-specific attribute.

### [`MEMORY_LIMIT`](@ref)

The algorithm stopped because it ran out of memory.

### [`OBJECTIVE_LIMIT`](@ref)

The algorithm stopped because it found a solution better than a minimum    limit set by the user.

This status may be returned in relation to the [`ObjectiveLimit`](@ref)    attribute, or some other solver-specific attribute.

### [`NORM_LIMIT`](@ref)

The algorithm stopped because the norm of an iterate became too large.

This typically means that the primal problem is unbounded, but that the    solver could not prove so.

### [`OTHER_LIMIT`](@ref)

The algorithm stopped due to a limit not covered by one of the `_LIMIT_`    statuses above.

### [`SLOW_PROGRESS`](@ref)

The algorithm stopped because it was unable to continue making progress    towards the solution.

### [`NUMERICAL_ERROR`](@ref)

The algorithm stopped because it encountered unrecoverable numerical error.

### [`INVALID_MODEL`](@ref)

The algorithm stopped because the model is invalid.

The reason for this return code is solver-specific, but common causes are    that the problem has zero variables or constraints, or that the problem data    contains an invalid number such as `NaN`.

### [`INVALID_OPTION`](@ref)

The algorithm stopped because it was provided an invalid option.

### [`INTERRUPTED`](@ref)

The algorithm stopped because of an interrupt signal.

This typically means that the solver was interrupted by the user with    `CTRL+C`.

### [`OTHER_ERROR`](@ref)

The algorithm stopped because of an error not covered by one of the statuses    defined above. Check the solver log for further details.
