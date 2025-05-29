```
partial_transpose(shadow::FactorizedShadow, subsystem::Vector{Int})::FactorizedShadow
```

Compute the partial transpose of a FactorizedShadow over the specified subsystem by swapping, for each site, the unprimed and primed indices using the `swapind` function. This function returns views of the underlying ITensors, avoiding unnecessary data duplication.

# Arguments

  * `shadow::FactorizedShadow`: The factorized classical shadow.
  * `subsystem::Vector{Int}`: A vector of 1-based site indices on which to perform the partial transpose.

# Returns

A new FactorizedShadow with the specified sites partially transposed.
