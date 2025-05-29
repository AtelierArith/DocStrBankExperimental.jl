```
FactorizedShadow(measurement_results::Vector{Int}, local_unitary::Vector{ITensor};
                 G::Vector{Float64} = fill(1.0, length(local_unitary)))
```

Construct a `FactorizedShadow` object from raw measurement results and unitary transformations.

# Arguments

  * `measurement_results::Vector{Int}`: Vector of binary measurement results for each qubit/site.
  * `local_unitary::Vector{ITensor}`: Vector of local unitary transformations applied during the measurement.
  * G::Vector{Float64}`(optional): Vector of`G` values for measurement error correction (default: 1.0 for all sites).

# Returns

A `FactorizedShadow` object.
