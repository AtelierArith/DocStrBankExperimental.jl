```
get_trace_moments(shadows::Array{<:AbstractShadow, 2}, kth_moments::Vector{Int}; O::Union{Nothing, MPO}=nothing)
```

Wrapper function. Compute multiple trace moments from an array of shadow objects.

# Arguments

  * `shadows::Array{<:AbstractShadow, 2}`: An array of shadow objects with dimensions `(n_ru, n_m)`.
  * `kth_moments::Vector{Int}`: A vector of moment orders.
  * `O::Union{Nothing, MPO}` (optional): An MPO observable; if provided, computes `Tr[O * ρ^k]` for each moment (default: `nothing`).

# Returns

A vector of trace moments corresponding to each moment in `kth_moments`.

# Example

```julia
moments = get_trace_moments(shadows_array, [1, 2, 3])
```
