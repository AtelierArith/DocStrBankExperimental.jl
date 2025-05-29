```julia
eachring(
    grid::SpeedyWeather.RingGrids.AbstractGridArray
) -> Any

```

Vector{UnitRange} `rings` は、グリッド `grid` のすべてのリングをループし、各リングごとに各グリッドポイントをループするために使用されます。使用例は次のとおりです。

```
rings = eachring(grid)
for ring in rings
    for ij in ring
        grid[ij]
```

事前に計算された `grid.rings` にアクセスします。
