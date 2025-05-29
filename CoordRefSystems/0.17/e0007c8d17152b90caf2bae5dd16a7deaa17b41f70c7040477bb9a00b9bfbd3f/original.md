```
Cartesian(x₁, x₂, ..., xₙ)
Cartesian{Datum}(x₁, x₂, ..., xₙ)
Cartesian((x₁, x₂, ..., xₙ))
Cartesian{Datum}((x₁, x₂, ..., xₙ))
```

N-dimensional Cartesian coordinates `x₁, x₂, ..., xₙ` in length units (default to meter) with a given `Datum` (default to `NoDatum`). The first 3 coordinates can be accessed with the properties `x`, `y` and `z`, respectively.

## Examples

```julia
Cartesian(1, 1) # add default units
Cartesian(1m, 1m) # integers are converted converted to floats
Cartesian(1.0km, 1.0km, 1.0km)
Cartesian{WGS84Latest}(1.0m, 1.0m)
```

## References

  * [Cartesian coordinate system](https://en.wikipedia.org/wiki/Cartesian_coordinate_system)
  * [ISO 80000-2:2019](https://www.iso.org/standard/64973.html)
  * [ISO 80000-3:2019](https://www.iso.org/standard/64974.html)
