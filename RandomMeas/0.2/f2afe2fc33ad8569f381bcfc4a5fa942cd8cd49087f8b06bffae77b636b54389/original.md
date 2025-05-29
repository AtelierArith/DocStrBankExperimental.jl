```
DenseShadow(measurement_probability::MeasurementProbability; G::Vector{Float64} = fill(1.0, length(u)))
```

Construct a `DenseShadow` object from a precomputed probability tensor.

# Arguments

  * `P::ITensor`: Probability tensor representing measurement results.
  * `u::Vector{ITensor}`: Vector of local unitary transformations.
  * `G::Vector{Float64}` (optional): Vector of G values to account for measurement errors (default: 1.0 for all sites).

# Returns

A `DenseShadow` object.
