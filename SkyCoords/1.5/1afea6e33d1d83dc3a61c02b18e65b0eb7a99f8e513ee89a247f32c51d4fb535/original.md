```
offset(::AbstractSkyCoords, AbstractSkyCoords) -> angle, angle
```

Return the separation and position angle in radians between two sky coordinates.

# Examples

```jldoctest
julia> c1 = ICRSCoords(0, 0); c2 = ICRSCoords(deg2rad(1), 0);

julia> offset(c1, c2) .|> rad2deg
(1.0, 90.0)
```

# See Also

  * [`separation`](@ref), [`position_angle`](@ref)
