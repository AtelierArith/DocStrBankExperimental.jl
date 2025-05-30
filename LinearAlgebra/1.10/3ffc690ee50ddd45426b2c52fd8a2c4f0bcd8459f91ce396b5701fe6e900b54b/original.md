```
Diagonal(A::AbstractMatrix)
```

Construct a matrix from the diagonal of `A`.

# Examples

```jldoctest
julia> A = permutedims(reshape(1:15, 5, 3))
3×5 Matrix{Int64}:
  1   2   3   4   5
  6   7   8   9  10
 11  12  13  14  15

julia> Diagonal(A)
3×3 Diagonal{Int64, Vector{Int64}}:
 1  ⋅   ⋅
 ⋅  7   ⋅
 ⋅  ⋅  13

julia> diag(A, 2)
3-element Vector{Int64}:
  3
  9
 15
```
