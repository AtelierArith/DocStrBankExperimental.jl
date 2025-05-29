```
partial_trace(shadows::AbstractArray{<:AbstractShadow}, subsystem::Vector{Int})
```

Compute the partial trace for each shadow in a collection of shadows.

# Arguments

  * `shadows::AbstractArray{<:AbstractShadow}`: A collection of shadow objects (vector or 2D array).
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem to retain.

# Returns

An array of shadows reduced to the specified subsystem, with the same dimensions as the input array.
