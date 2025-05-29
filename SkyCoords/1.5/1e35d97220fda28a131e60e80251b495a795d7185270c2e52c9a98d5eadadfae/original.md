```
position_angle(c1::AbstractSkyCoords, c2::AbstractSkyCoords) -> angle
```

Return position angle between two sky coordinates, in positive radians.

# Examples

```jldoctest
julia> c1 = ICRSCoords(0, 0); c2 = ICRSCoords(deg2rad(1), 0);

julia> position_angle(c1, c2) |> rad2deg
90.0
```
