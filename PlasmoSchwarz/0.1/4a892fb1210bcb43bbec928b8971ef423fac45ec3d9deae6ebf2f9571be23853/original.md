```
calculate_dual_feasibility(algorithm::SchwarzAlgorithm) -> Vector{Float64}
```

Evaluate the dual feasibility of the linking constraints defined over the  algorithm's graph. For each linking constraint, the function calculates the  difference between the maximum and minimum dual values across subproblems.

Args:

  * `algorithm::SchwarzAlgorithm`: The algorithm object containing the graph and linking constraints.

Returns:     A vector of dual residuals for the linking constraints.
