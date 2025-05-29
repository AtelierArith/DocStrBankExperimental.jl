```
Block(inds...)
```

`Block`は、インデックスまたは列挙型のセットをラップする単純なもので、ディスパッチに使用できるようにします。`AbstractBlockArray`を`Block`でインデックス指定すると、そのブロックインデックスのブロックが返され、単一の要素ではなくなります。

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
