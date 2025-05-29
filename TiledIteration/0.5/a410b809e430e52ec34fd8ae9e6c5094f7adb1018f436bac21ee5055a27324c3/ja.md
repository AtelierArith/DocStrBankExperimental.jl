```
RelaxStride(tilesize)
```

タイル戦略で、各タイルのサイズが `tilesize` であることを保証します。必要なタイルがわずかに重なる場合でも、すべてをカバーします。

# 例

```jldoctest
julia> using TiledIteration

julia> collect(TileIterator((1:4,), RelaxStride((2,))))
2-element Array{Tuple{UnitRange{Int64}},1}:
 (1:2,)
 (3:4,)

julia> collect(TileIterator((1:4,), RelaxStride((3,))))
2-element Array{Tuple{UnitRange{Int64}},1}:
 (1:3,)
 (2:4,)
```

詳細は [`TileIterator`](@ref) を参照してください。
