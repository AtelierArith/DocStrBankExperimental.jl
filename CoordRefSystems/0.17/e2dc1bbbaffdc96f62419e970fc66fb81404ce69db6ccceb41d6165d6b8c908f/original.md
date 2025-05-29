```
Cartesian2D(x, y)
Cartesian2D{Datum}(x, y)
Cartesian2D((x, y))
Cartesian2D{Datum}((x, y))
```

Alias to [`Cartesian`](@ref) with 2 coordinates.

## Examples

```julia
Cartesian2D(1, 1) # add default units
Cartesian2D(1m, 1m) # integers are converted converted to floats
Cartesian2D(1.0km, 1.0km)
Cartesian2D{WGS84Latest}(1.0m, 1.0m)
```
