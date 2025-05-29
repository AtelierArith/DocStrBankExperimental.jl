```julia
eachring(
    grid1::SpeedyWeather.RingGrids.AbstractGridArray,
    grids::SpeedyWeather.RingGrids.AbstractGridArray...
) -> Any

```

Same as `eachring(grid)` but performs a bounds check to assess that all `grids` according to `grids_match` (non-parametric grid type, nlat_half and length).
