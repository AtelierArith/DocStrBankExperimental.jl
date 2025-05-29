```
hexneighbors(hex::Hexagon)
```

Return the neighbors of `hex`.

For more information about making hexagons and hexagonal grids, see [Luxor.Hexagon](@ref).

## Example

```julia
julia> h = HexagonOffsetEvenR(0, 0, 70.0);

julia> hexneighbors(h)
HexagonNeighborIterator(HexagonCubic(0, 0, 0, Point(0.0, 0.0), 70.0, 70.0))

julia> collect(hexneighbors(h))
6-element Vector{Any}:
 HexagonCubic(1, -1, 0, Point(0.0, 0.0), 70.0, 70.0)
 HexagonCubic(1, 0, -1, Point(0.0, 0.0), 70.0, 70.0)
 HexagonCubic(0, 1, -1, Point(0.0, 0.0), 70.0, 70.0)
 HexagonCubic(-1, 1, 0, Point(0.0, 0.0), 70.0, 70.0)
 HexagonCubic(-1, 0, 1, Point(0.0, 0.0), 70.0, 70.0)
 HexagonCubic(0, -1, 1, Point(0.0, 0.0), 70.0, 70.0)
```
