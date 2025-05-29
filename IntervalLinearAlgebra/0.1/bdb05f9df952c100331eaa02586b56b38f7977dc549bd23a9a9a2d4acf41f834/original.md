```
is_H_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

Tests whether the square interval matrix A is an H-matrix, by testing that $⟨A⟩^{-1}e>0$, where $e=[1, 1, …, 1]ᵀ$. Note that in practice it tests that a *floating point approximation* of $⟨A⟩^{-1}e$ satisfies the condition. For more details see section 4.4 of [[HOR19]](@ref).

### Examples

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> is_H_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_H_matrix(A)
false
```
