```
is_Z_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

Checks whether the square interval matrix $A$ is a Z-matrix, that is whether $Aᵢⱼ≤0$ for all $i≠j$. For more details see section 4.2 of [[HOR19]](@ref).

### Examples

```jldoctest
julia> A = [2..4 -2.. -1; -2.. -1 2..4]
2×2 Matrix{Interval{Float64}}:
   [2, 4]  [-2, -1]
 [-2, -1]    [2, 4]

julia> is_Z_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_Z_matrix(A)
false
```
