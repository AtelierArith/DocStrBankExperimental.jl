```
RelaxStride(tilesize)
```

Tiling strategy, that guarantees each tile of size `tilesize`. If the needed tiles will slightly overlap, to cover everything.

# Examples

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

See also [`TileIterator`](@ref).
