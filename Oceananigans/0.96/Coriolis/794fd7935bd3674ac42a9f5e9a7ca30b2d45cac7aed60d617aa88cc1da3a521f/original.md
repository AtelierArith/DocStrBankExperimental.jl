```
BetaPlane([FT=Float64;] f₀=nothing, β=nothing,
          rotation_rate=Ω_Earth, latitude=nothing, radius=R_Earth)
```

Return a $β$-plane Coriolis parameter, $f = f₀ + β y$ with floating-point type `FT`.

The user may specify both `f₀` and `β`, or the three parameters `rotation_rate`, `latitude` (in degrees), and `radius` that specify the rotation rate and radius of a planet, and the central latitude (where $y = 0$) at which the `β`-plane approximation is to be made.

If `f₀` and `β` are not specified, they are calculated from `rotation_rate`, `latitude`, and `radius` according to the relations `f₀ = 2 * rotation_rate * sind(latitude)` and `β = 2 * rotation_rate * cosd(latitude) / radius`.

By default, the `rotation_rate` and planet `radius` are assumed to be Earth's.
