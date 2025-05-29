```
Mercator(x, y)
Mercator{Datum}(x, y)
```

Mercator coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
Mercator(1, 1) # add default units
Mercator(1m, 1m) # integers are converted converted to floats
Mercator(1.0km, 1.0km) # length quantities are converted to meters
Mercator(1.0m, 1.0m)
Mercator{WGS84Latest}(1.0m, 1.0m)
```

See [EPSG:3395](https://epsg.io/3395).
