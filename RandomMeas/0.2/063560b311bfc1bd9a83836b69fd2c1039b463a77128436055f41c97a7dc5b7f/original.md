```
get_trace_moments(shadows::Vector{<:AbstractShadow}, kth_moments::Vector{Int}; O::Union{Nothing, MPO}=nothing)
```

Wrapper function. Compute multiple trace moments from a vector of shadow objects by reshaping the vector into a 2D array.

# Arguments

  * `shadows::Vector{<:AbstractShadow}`: A vector of shadow objects.
  * `kth_moments::Vector{Int}`: A vector of moment orders.
  * `O::Union{Nothing, MPO}` (optional): An MPO observable.

# Returns

A vector of trace moments.

# Example

```julia
moments = get_trace_moments(shadows_vector, [1, 2, 3])
```
