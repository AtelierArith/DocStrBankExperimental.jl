```
estimate_ordinal_model_probabilities(df, table)
```

Estimates the probabilities of an ordinal loglinear model based on the observed cell counts.

# Arguments

  * `df::DataFrame`: The data frame containing the predictor variables.
  * `table::AbstractMatrix`: The matrix of predictor values for which probabilities are to be estimated.

# Returns

  * `prob::Vector{Float64}`: A vector of estimated probabilities.
