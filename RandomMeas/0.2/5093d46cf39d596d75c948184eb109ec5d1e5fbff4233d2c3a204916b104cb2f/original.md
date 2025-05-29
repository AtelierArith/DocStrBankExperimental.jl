```
partial_transpose(shadows::AbstractArray{<:AbstractShadow}, subsystem::Vector{Int})
```

Compute the partial transpose for each shadow in a collection.

# Arguments

  * `shadows::AbstractArray{<:AbstractShadow}`: A collection (vector or 2D array) of shadow objects.
  * `subsystem::Vector{Int}`: A vector of site indices (1-based) specifying the subsystem(s) over which the transpose is to be performed.

# Returns

An array of shadow objects with the partial transpose applied, preserving the input dimensions.
