```
calculate_primal_feasibility(algorithm::SchwarzAlgorithm) -> Vector{Float64}
```

Evaluate the primal feasibility of the linking constraints defined over the  algorithm's graph. This is done by checking the residuals between the linking  constraints and their expected values based on the subproblem solutions.

Args:

  * `algorithm::SchwarzAlgorithm`: The algorithm object containing the graph and linking constraints.

Returns:     A vector of primal residuals for the linking constraints.
