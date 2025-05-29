```
offset(::AbstractSkyCoords, separation, pa) -> coordinate
```

Offset a coordinate by a given angular separation, `separation`, in radians and position angle, `pa`, in radians.

Uses the sine and cosine rules in spherical coordinates with corrections for the antipodes. Returns a sky coordinate of the same type as input.

# Examples

```jldoctest
julia> c1 = ICRSCoords(0, 0);

julia> c2 = offset(c1, deg2rad(1), deg2rad(90))
ICRSCoords{Float64}(0.017453292519943295, 1.0686516840418957e-18)

julia> offset(c1, c2) .|> rad2deg
(1.0, 90.0)
```

# See Also

  * [`separation`](@ref), [`position_angle`](@ref)
