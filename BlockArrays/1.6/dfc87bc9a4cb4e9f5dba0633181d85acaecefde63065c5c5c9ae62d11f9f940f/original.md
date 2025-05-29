```
blocksize(A::AbstractArray)
blocksize(A::AbstractArray, i::Int)
```

Return the tuple of the number of blocks along each dimension. See also size and blocksizes.

# Examples

```jldoctest
julia> A = BlockArray(ones(3,3),[2,1],[1,1,1])
2×3-blocked 3×3 BlockMatrix{Float64}:
 1.0  │  1.0  │  1.0
 1.0  │  1.0  │  1.0
 ─────┼───────┼─────
 1.0  │  1.0  │  1.0

julia> blocksize(A)
(2, 3)

julia> blocksize(A,2)
3
```
