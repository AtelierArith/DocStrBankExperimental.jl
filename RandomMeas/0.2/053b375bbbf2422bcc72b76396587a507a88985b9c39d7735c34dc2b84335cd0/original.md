```
ShallowShadow(measurement_results::Vector{Int}, local_unitary::Vector{ITensor};
                 G::Vector{Float64} = fill(1.0, length(local_unitary)))
```

Construct a `ShallowSShadow` object from raw measurement results and unitary transformations.

# Arguments

  * `measurement_results::Vector{Int}`: Vector of binary measurement results for each qubit/site.
  * `local_unitary::Vector{ITensor}`: Vector of local unitary transformations applied during the measurement.

# Returns

A `ShallowShadow` object.
