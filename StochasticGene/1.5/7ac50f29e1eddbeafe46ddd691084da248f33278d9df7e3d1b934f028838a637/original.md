```
predictedfn(param, data::RNAData, model::AbstractGeneTransitionModel)
```

Calculates the likelihood for a single RNA histogram.

# Arguments

  * `param`: The model parameters.
  * `data::RNAData`: The RNA data.
  * `model::AbstractGeneTransitionModel`: The model.

# Returns

  * `Vector{Float64}`: The steady-state probabilities for the RNA histogram.
