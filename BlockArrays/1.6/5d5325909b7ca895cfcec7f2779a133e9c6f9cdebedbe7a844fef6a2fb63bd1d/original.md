```
blocksizes(A::AbstractArray)
blocksizes(A::AbstractArray, d::Integer)
```

Return an iterator over the sizes of each block. See also size and blocksize.

# Examples

```jldoctest
julia> A = BlockArray(ones(3,3),[2,1],[1,1,1])
2×3-blocked 3×3 BlockMatrix{Float64}:
 1.0  │  1.0  │  1.0
 1.0  │  1.0  │  1.0
 ─────┼───────┼─────
 1.0  │  1.0  │  1.0

julia> blocksizes(A)
2×3 BlockArrays.BlockSizes{Tuple{Int64, Int64}, 2, BlockMatrix{Float64, Matrix{Matrix{Float64}}, Tuple{BlockedOneTo{Int64, Vector{Int64}}, BlockedOneTo{Int64, Vector{Int64}}}}}:
 (2, 1)  (2, 1)  (2, 1)
 (1, 1)  (1, 1)  (1, 1)

julia> blocksizes(A)[1,2]
(2, 1)

julia> blocksizes(A,2)
3-element Vector{Int64}:
 1
 1
 1
```
