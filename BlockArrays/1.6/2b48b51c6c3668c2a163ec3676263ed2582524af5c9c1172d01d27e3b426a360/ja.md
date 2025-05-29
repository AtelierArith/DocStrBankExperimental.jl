```
BlockedMatrix{T}
```

`BlockedArray{T, 2}` のエイリアス

```jldoctest
julia> A = reshape([1:6;], 2, 3)
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> BlockedMatrix(A, [1,1], [1,2])
2×2-blocked 2×3 BlockedMatrix{Int64}:
 1  │  3  5
 ───┼──────
 2  │  4  6
```
