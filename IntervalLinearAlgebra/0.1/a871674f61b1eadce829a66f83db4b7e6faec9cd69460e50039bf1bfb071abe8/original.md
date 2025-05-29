```
is_M_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

Checks whether the square interval matrix $A$ is an M-matrix, that is a Z-matrix with non-negative inverse. For more details see section 4.2 of [[HOR19]](@ref).

### Examples

```jldoctest
julia> A = [2..2 -1..0; -1..0 2..2]
2×2 Matrix{Interval{Float64}}:
  [2, 2]  [-1, 0]
 [-1, 0]   [2, 2]

julia> is_M_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_M_matrix(A)
false
```
