```
RelaxLastTile(tilesize)
```

タイル戦略で、必要に応じて各次元の最後のタイルのサイズを `tilesize` より小さくすることを許可します。他のすべてのタイルはサイズ `tilesize` です。

# 例

```jldoctest
julia> using TiledIteration

julia> collect(TileIterator((1:4,), RelaxLastTile((2,))))
2-element Array{Tuple{UnitRange{Int64}},1}:
 (1:2,)
 (3:4,)

julia> collect(TileIterator((1:7,), RelaxLastTile((2,))))
4-element Array{Tuple{UnitRange{Int64}},1}:
 (1:2,)
 (3:4,)
 (5:6,)
 (7:7,)
```

詳細は [`TileIterator`](@ref) を参照してください。
