```
Block(inds...)
```

A `Block` is simply a wrapper around a set of indices or enums so that it can be used to dispatch on. By indexing a `AbstractBlockArray` with a `Block` the a block at that block index will be returned instead of a single element.

```jldoctest
julia> A = BlockArray(ones(2,3), [1, 1], [2, 1])
2×2-blocked 2×3 BlockMatrix{Float64}:
 1.0  1.0  │  1.0
 ──────────┼─────
 1.0  1.0  │  1.0

julia> A[Block(1, 1)]
1×2 Matrix{Float64}:
 1.0  1.0
```
