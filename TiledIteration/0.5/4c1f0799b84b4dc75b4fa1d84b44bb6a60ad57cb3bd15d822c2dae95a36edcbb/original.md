```
titr = TileIterator(axes::NTuple{N, AbstractUnitRange}, strategy)
```

Decompose `axes` into an iterator `titr` of smaller axes according to `strategy`.

The `strategy` argument controls the details of the tiling. For instance if the length of an axis is not divisible by the tile size, what should happen? One approach would be to relax the size requirement for the last tile. Another possibility to relax the `stride` so that all tiles are of the requested size, but tiles may be slightly overlapping. These two possibilities are implemented by [`RelaxLastTile`](@ref) and [`RelaxStride`](@ref).

# Examples

```jldoctest
julia> using TiledIteration

julia> collect(TileIterator((1:3, 0:5), RelaxLastTile((2, 3))))
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (3:3, 0:2)  (3:3, 3:5)

julia> collect(TileIterator((1:3, 0:5), (2, 3))) # defaults to RelaxLastTile
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (3:3, 0:2)  (3:3, 3:5)

julia> collect(TileIterator((1:3, 0:5), RelaxStride((2, 3))))
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (2:3, 0:2)  (2:3, 3:5)
```
