```
optimal_branching_rule(table::BranchingTable, variables::Vector, problem::AbstractProblem, measure::AbstractMeasure, solver::AbstractSetCoverSolver)::OptimalBranchingResult
```

Generate an optimal branching rule from a given branching table.

### Arguments

  * `table`: A [`BranchingTable`](@ref) instance containing candidate clauses.
  * `variables`: A vector of variables to perform the branching.
  * `problem`: The problem instance being solved.
  * `measure`: The measure used for evaluating the problem size reduction in the branches.
  * `solver`: The solver used for the weighted minimum set cover problem, which can be either [`LPSolver`](@ref) or [`IPSolver`](@ref).

### Returns

A [`OptimalBranchingResult`](@ref) object representing the optimal branching rule.
