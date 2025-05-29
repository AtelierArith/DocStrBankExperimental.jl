```
rref(A::AbstractMatrix{T}) where {T<:Interval}
```

Computes the reduced row echelon form of the interval matrix `A` using maximum mignitude as pivoting strategy.

### Examples

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> rref(A)
2×2 Matrix{Interval{Float64}}:
 [2, 4]  [-1, 1]
 [0, 0]       [1.5, 4.5]
```
