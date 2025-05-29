```
Polar(ρ, ϕ)
Polar{Datum}(ρ, ϕ)
```

Polar coordinates with radius `ρ ∈ [0,∞)` in length units (default to meter), angle `ϕ ∈ [0,2π)` in angular units (default to radian) and a given `Datum` (default to `NoDatum`).

## Examples

```julia
Polar(1, π/4) # add default units
Polar(1m, (π/4)rad) # integers are converted converted to floats
Polar(1.0m, 45°) # degrees are converted to radians
Polar(1.0km, (π/4)rad)
Polar{WGS84Latest}(1.0m, (π/4)rad)
```

## References

  * [Polar coordinate system](https://en.wikipedia.org/wiki/Polar_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
