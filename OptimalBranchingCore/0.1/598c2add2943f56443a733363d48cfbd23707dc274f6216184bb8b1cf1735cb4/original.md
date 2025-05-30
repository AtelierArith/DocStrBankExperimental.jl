```
branching_table(problem::AbstractProblem, table_solver::AbstractTableSolver, variables::Vector{Int})
```

Obtains the branching table for a given problem using a specified table solver.

### Arguments

  * `problem`: The problem instance.
  * `table_solver`: The table solver, which is a subtype of [`AbstractTableSolver`](@ref).
  * `variables`: A vector of indices of the variables to be considered for the branching table.

### Returns

A branching table, which is a [`BranchingTable`](@ref) object.
