```julia
spherical_distance(
    Formula::Type{<:SpeedyWeather.RingGrids.AbstractSphericalDistance},
    args...;
    kwargs...
) -> Any

```

2点 `lonlat1` と `lonlat2` の間の球面距離、または大円距離を、`Formula`（デフォルトは `Haversine`）を使用して計算します。
