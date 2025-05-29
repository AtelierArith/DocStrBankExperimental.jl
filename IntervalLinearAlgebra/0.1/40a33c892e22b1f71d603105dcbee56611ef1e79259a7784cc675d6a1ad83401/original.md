```
interval_norm(A::AbstractVector{T}) where {T<:Interval}
```

computes the infinity norm of interval vector $v$.

### Examples

```jldoctest
julia> b = [-2..2, -3..2]
2-element Vector{Interval{Float64}}:
 [-2, 2]
 [-3, 2]

julia> interval_norm(b)
3.0
```
