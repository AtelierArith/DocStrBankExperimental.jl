```julia
coriolis(
    grid::SpeedyWeather.RingGrids.AbstractGridArray;
    kwargs...
) -> Any

```

Return the Coriolis parameter `f` on a grid like `grid` on a planet of `rotation` [1/s]. Default rotation of Earth.
