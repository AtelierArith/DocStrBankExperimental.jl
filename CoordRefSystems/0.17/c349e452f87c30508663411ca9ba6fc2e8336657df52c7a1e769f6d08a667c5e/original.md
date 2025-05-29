```
Spherical(r, θ, ϕ)
Spherical{Datum}(r, θ, ϕ)
```

Spherical coordinates with radius `r ∈ [0,∞)` in length units (default to meter),  polar angle `θ ∈ [0,π]` and azimuth angle `ϕ ∈ [0,2π)` in angular units (default to radian) and a given `Datum` (default to `NoDatum`).

## Examples

```julia
Spherical(1, π/4, π/4) # add default units
Spherical(1m, (π/4)rad, (π/4)rad) # integers are converted converted to floats
Spherical(1.0m, 45°, 45°) # degrees are converted to radians
Spherical(1.0km, (π/4)rad, (π/4)rad)
Spherical{WGS84Latest}(1.0m, (π/4)rad, (π/4)rad)
```

## References

  * [Spherical coordinate system](https://en.wikipedia.org/wiki/Spherical_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
