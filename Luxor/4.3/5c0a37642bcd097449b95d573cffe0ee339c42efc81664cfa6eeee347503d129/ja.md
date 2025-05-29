```
hexneighbors(hex::Hexagon)
```

`hex`の隣接する六角形を返します。

六角形と六角形グリッドの作成に関する詳細は、[Luxor.Hexagon](@ref)を参照してください。

## 例

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
