```
BlockedVector{T}
```

Alias for `BlockedArray{T, 1}`

```jldoctest
julia> A = [1:6;]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> BlockedVector(A, [3,2,1])
3-blocked 6-element BlockedVector{Int64}:
 1
 2
 3
 ─
 4
 5
 ─
 6
```
