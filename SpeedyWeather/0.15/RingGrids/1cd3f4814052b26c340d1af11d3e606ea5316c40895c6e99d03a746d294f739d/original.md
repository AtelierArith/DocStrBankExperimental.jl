```julia
spherical_distance(
    Formula::Type{<:SpeedyWeather.RingGrids.AbstractSphericalDistance},
    args...;
    kwargs...
) -> Any

```

Spherical distance, or great-circle distance, between two points `lonlat1` and `lonlat2` using the `Formula` (default `Haversine`).
