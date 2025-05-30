```
OptimalBranchingResult{INT <: Integer}
```

The result type for the optimal branching rule.

### Fields

  * `optimal_rule::DNF{INT}`: The optimal branching rule.
  * `branching_vector::Vector{T<:Real}`: The branching vector that records the size reduction in each subproblem.
  * `γ::Float64`: The optimal γ value (the complexity of the branching rule).
