```julia
eachgrid(
    grid::SpeedyWeather.RingGrids.AbstractGridArray
) -> Any

```

CartesianIndices for the 2nd to last dimension of an AbstractGridArray, to be used like

for k in eachgrid(grid)     for ring in eachring(grid)         for ij in ring             grid[ij, k]
