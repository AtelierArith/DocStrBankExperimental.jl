```
interval_norm(A::AbstractMatrix{T}) where {T<:Interval}
```

computes the infinity norm of interval matrix $A$.

### Examples

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> interval_norm(A)
5.0
```
