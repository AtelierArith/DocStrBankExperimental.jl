```
eachblock(A::AbstractBlockArray)
```

`AbstractBlockArray`の各ブロックを反復処理し、ビューを返すジェネレーターを作成します。

```jldoctest
julia> v = Array(reshape(1:6, (2, 3)))
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> A = BlockArray(v, [1,1], [2,1])
2×2-blocked 2×3 BlockMatrix{Int64}:
 1  3  │  5
 ──────┼───
 2  4  │  6

julia> sum.(eachblock(A))
2×2 Matrix{Int64}:
 4  5
 6  6
```
