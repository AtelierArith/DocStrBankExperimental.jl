```
sample(model::AutoRegressionEmission, Y_prev::Matrix{<:Real}; observation_sequence::Matrix{<:Real}=Matrix{Float64}(undef, 0, model.output_dim))
```

Generate a sample from the given autoregressive emission model using the previous observations `Y_prev`, and append it to the provided observation sequence.

# Arguments

  * `model::AutoRegressionEmission`: The autoregressive emission model to sample from.
  * `Y_prev::Matrix{<:Real}`: The matrix of previous observations, where each row represents an observation.
  * `observation_sequence::Matrix{<:Real}`: The sequence of observations to which the new sample will be appended (defaults to an empty matrix with appropriate dimensions).

# Returns

  * `Matrix{Float64}`: The updated observation sequence with the new sample appended.
