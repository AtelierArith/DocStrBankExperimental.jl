```
test_rule(table::BranchingTable, predicted::DNF, problem::AbstractProblem, m::AbstractMeasure, variables::Vector)
```

Test the validity and complexity of a rule.

### Arguments

  * `table::BranchingTable`: The branching table.
  * `predicted::DNF`: The logic expression in DNF.
  * `problem::AbstractProblem`: The problem.
  * `m::AbstractMeasure`: The measure.
  * `variables::Vector`: The variables.

### Returns

  * `is_valid::Bool`: Whether the rule is valid.
  * `gamma::Float64`: The complexity of the rule.
