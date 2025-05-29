```
partial_trace(shadow::DenseShadow, subsystem::Vector{Int})
```

Compute the partial trace of a `DenseShadow` object over the complement of the specified subsystem.

# Arguments

  * `shadow::DenseShadow`: The dense shadow to compute the partial trace for.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns

A new `DenseShadow` object reduced to the specified subsystem.
