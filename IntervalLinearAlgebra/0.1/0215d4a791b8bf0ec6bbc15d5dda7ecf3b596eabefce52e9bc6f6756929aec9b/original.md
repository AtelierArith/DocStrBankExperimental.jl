```
is_strongly_regular(A::AbstractMatrix{T}) where {T<:Interval}
```

Tests whether the square interval matrix $A$ is strongly regular, i.e. if $A_c^{-1}A$ is an H-matrix, where $A_c$ is the midpoint matrix of $A$`. For more details see section 4.6 of [[HOR19]](@ref).

### Examples

```jldoctest
julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_strongly_regular(A)
true

julia> A = [0..2 1..1;-1.. -1 0..2]
2×2 Matrix{Interval{Float64}}:
   [0, 2]  [1, 1]
 [-1, -1]  [0, 2]

julia> is_strongly_regular(A)
false
```
