```
blocksize(A::AbstractArray)
blocksize(A::AbstractArray, i::Int)
```

各次元に沿ったブロックの数のタプルを返します。sizeおよびblocksizesも参照してください。

# 例

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
