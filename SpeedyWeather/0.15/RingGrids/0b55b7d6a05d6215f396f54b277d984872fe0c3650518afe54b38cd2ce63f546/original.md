```julia
eachring(
    grid::SpeedyWeather.RingGrids.AbstractGridArray
) -> Any

```

Vector{UnitRange} `rings` to loop over every ring of grid `grid` and then each grid point per ring. To be used like

```
rings = eachring(grid)
for ring in rings
    for ij in ring
        grid[ij]
```

Accesses precomputed `grid.rings`.
