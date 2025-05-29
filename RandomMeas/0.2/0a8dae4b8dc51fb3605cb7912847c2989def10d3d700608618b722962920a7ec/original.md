```
get_trace_moment(shadows::Array{<:AbstractShadow, 2}, kth_moment::Int; O::Union{Nothing, MPO}=nothing)
```

Compute a single trace moment from an array of `AbstractShadow` objects.

# Arguments

  * `shadows::Array{<:AbstractShadow, 2}`: An array of shadow objects with dimensions `(n_ru, n_m)`, where `n_ru` is the number of random unitaries and `n_m` is the number of measurements.
  * `kth_moment::Int`: The moment `k` to compute (e.g., `k = 1, 2, ...`).
  * `O::Union{Nothing, MPO}` (optional): If provided, computes `Tr[O * ρ^k]`; otherwise, computes `Tr[ρ^k]` (default: `nothing`).

# Returns

The computed trace moment as a scalar.

# Example

```julia
moment1 = get_trace_moment(shadows, 1)
moment2 = get_trace_moment(shadows, 2; O=my_operator)
```
