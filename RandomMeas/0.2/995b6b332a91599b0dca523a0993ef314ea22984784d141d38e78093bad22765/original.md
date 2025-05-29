```
get_trace_moment(shadows::Vector{<:AbstractShadow}, kth_moment::Int; O::Union{Nothing, MPO}=nothing)
```

Wrapper function. Compute a single trace moment for a vector of shadow objects by reshaping the vector into a 2D array.

# Arguments

  * `shadows::Vector{<:AbstractShadow}`: A vector of shadow objects.
  * `kth_moment::Int`: The moment order `k` to compute.
  * `O::Union{Nothing, MPO}` (optional): An MPO observable.

# Returns

The computed trace moment as a scalar.

# Example

```julia
moment = get_trace_moment(shadows_vector, 2; O=my_operator)
```
