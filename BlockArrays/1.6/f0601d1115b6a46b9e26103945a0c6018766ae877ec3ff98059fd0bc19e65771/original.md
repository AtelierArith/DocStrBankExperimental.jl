```
blockaxes(A::AbstractArray)
```

Return the tuple of valid block indices for array `A`.

# Examples

```jldoctest
julia> A = BlockArray([1,2,3],[2,1])
2-blocked 3-element BlockVector{Int64}:
 1
 2
 ─
 3

julia> blockaxes(A)
(BlockRange(Base.OneTo(2)),)

julia> B = BlockArray(zeros(3,4), [1,2], [1,2,1])
2×3-blocked 3×4 BlockMatrix{Float64}:
 0.0  │  0.0  0.0  │  0.0
 ─────┼────────────┼─────
 0.0  │  0.0  0.0  │  0.0
 0.0  │  0.0  0.0  │  0.0

julia> blockaxes(B)
(BlockRange(Base.OneTo(2)), BlockRange(Base.OneTo(3)))
```
