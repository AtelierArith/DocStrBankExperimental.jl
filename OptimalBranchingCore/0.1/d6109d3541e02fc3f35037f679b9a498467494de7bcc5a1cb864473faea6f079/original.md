```
BranchingStrategy
BranchingStrategy(; kwargs...)
```

A struct representing the configuration for a solver, including the reducer and branching strategy.

### Fields

  * `table_solver::AbstractTableSolver`: The solver to resolve the relevant bit strings and generate a branching table.
  * `set_cover_solver::AbstractSetCoverSolver = IPSolver()`: The solver to solve the set covering problem.
  * `selector::AbstractSelector`: The selector to select the next branching variable or decision.
  * `m::AbstractMeasure`: The measure to evaluate the performance of the branching strategy.
