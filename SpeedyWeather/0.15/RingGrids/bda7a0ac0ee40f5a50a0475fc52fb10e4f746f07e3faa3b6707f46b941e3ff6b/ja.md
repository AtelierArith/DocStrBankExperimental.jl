```julia
eachgrid(
    grid::SpeedyWeather.RingGrids.AbstractGridArray
) -> Any

```

AbstractGridArrayの2番目から最後の次元のCartesianIndicesで、次のように使用されます。

for k in eachgrid(grid)     for ring in eachring(grid)         for ij in ring             grid[ij, k]
