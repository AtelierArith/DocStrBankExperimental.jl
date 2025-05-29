```
Summary(results::Results;interval::Int=95,digits::Int=3)
```

Generate summary statistics for results: point estimates and credible intervals for edge coefficients, probabilities of influence for individual nodes

# Arguments

  * `results`: a Results object, returned from running [`Fit!`](@ref)
  * `interval`: (optional) Integer, level for credible intervals. Default is 95%.
  * `digits`: (optional) Integer, number of digits (after the decimal) to round results to. Default is 3.

# Returns

A BNRSummary object containing a matrix of edge coefficient point estimates (`coef_matrix`), a matrix of edge coefficient credible intervals (`ci_matrix`), and a DataFrame  containing the probability of influence of each node (`pi_nodes`).
