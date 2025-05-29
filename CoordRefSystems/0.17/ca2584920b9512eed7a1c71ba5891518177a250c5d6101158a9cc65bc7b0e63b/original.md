```
Lambert(x, y)
Lambert{Datum}(x, y)
```

Lambert cylindrical equal-area coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
Lambert(1, 1) # add default units
Lambert(1m, 1m) # integers are converted converted to floats
Lambert(1.0km, 1.0km) # length quantities are converted to meters
Lambert(1.0m, 1.0m)
Lambert{WGS84Latest}(1.0m, 1.0m)
```

See [ESRI:54034](https://epsg.io/54034).
