```
NonTraditionalBetaPlane(FT=Float64;
                        fz=nothing, fy=nothing, β=nothing, γ=nothing,
                        rotation_rate=Ω_Earth, latitude=nothing, radius=R_Earth)
```

The user may directly specify `fz`, `fy`, `β`, `γ`, and `radius` or the three parameters `rotation_rate`, `latitude` (in degrees), and `radius` that specify the rotation rate and radius of a planet, and the central latitude (where $y = 0$) at which the non-traditional `β`-plane approximation is to be made.

If `fz`, `fy`, `β`, and `γ` are not specified, they are calculated from `rotation_rate`, `latitude`, and `radius` according to the relations `fz = 2 * rotation_rate * sind(latitude)`, `fy = 2 * rotation_rate * cosd(latitude)`, `β = 2 * rotation_rate * cosd(latitude) / radius`, and `γ = - 4 * rotation_rate * sind(latitude) / radius`.

By default, the `rotation_rate` and planet `radius` is assumed to be Earth's.
