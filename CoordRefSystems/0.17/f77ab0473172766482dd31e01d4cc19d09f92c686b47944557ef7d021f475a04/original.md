```
Cylindrical(ρ, ϕ, z)
Cylindrical{Datum}(ρ, ϕ, z)
```

Cylindrical coordinates with radius `ρ ∈ [0,∞)` in length units (default to meter),  angle `ϕ ∈ [0,2π)` in angular units (default to radian), height `z ∈ [0,∞)` in length units (default to meter) and a given `Datum` (default to `NoDatum`).

## Examples

```julia
Cylindrical(1, π/4, 1) # add default units
Cylindrical(1m, (π/4)rad, 1m) # integers are converted converted to floats
Cylindrical(1.0m, 45°, 1.0m) # degrees are converted to radians
Cylindrical(1.0km, (π/4)rad, 1.0km)
Cylindrical{WGS84Latest}(1.0m, (π/4)rad, 1.0m)
```

## References

  * [Cylindrical coordinate system](https://en.wikipedia.org/wiki/Cylindrical_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
