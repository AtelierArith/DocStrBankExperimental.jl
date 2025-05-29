```
Cartesian3D(x, y, z)
Cartesian3D{Datum}(x, y, z)
Cartesian3D((x, y, z))
Cartesian3D{Datum}((x, y, z))
```

Alias to [`Cartesian`](@ref) with 3 coordinates.

## Examples

```julia
Cartesian3D(1, 1, 1) # add default units
Cartesian3D(1m, 1m, 1m) # integers are converted converted to floats
Cartesian3D(1.0km, 1.0km, 1.0km)
Cartesian3D{WGS84Latest}(1.0m, 1.0m, 1.0m)
```
