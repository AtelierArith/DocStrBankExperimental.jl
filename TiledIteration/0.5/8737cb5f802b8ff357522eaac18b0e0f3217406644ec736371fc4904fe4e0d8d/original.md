```
RelaxLastTile(tilesize)
```

Tiling strategy, that permits the size of the last tiles along each dimension to be smaller than `tilesize` if needed. All other tiles are of size `tilesize`.

# Examples

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

See also [`TileIterator`](@ref).
