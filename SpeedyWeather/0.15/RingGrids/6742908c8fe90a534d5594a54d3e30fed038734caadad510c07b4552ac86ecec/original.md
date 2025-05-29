```julia
eachring(
    Grid::Type{<:SpeedyWeather.RingGrids.AbstractGridArray},
    nlat_half::Integer
) -> Any

```

Computes the ring indices `i0:i1` for start and end of every longitudinal point on a given ring `j` of `Grid` at resolution `nlat_half`. Used to loop over rings of a grid. These indices are also precomputed in every `grid.rings`.
