```julia
coriolis(
    grid::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

Return the Coriolis parameter `f` on the grid `Grid` of resolution `nlat_half` on a planet of `rotation` [1/s]. Default rotation of Earth.
