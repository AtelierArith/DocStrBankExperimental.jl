```
Robinson(x, y)
Robinson{Datum}(x, y)
```

Robinson coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
Robinson(1, 1) # add default units
Robinson(1m, 1m) # integers are converted converted to floats
Robinson(1.0km, 1.0km) # length quantities are converted to meters
Robinson(1.0m, 1.0m)
Robinson{WGS84Latest}(1.0m, 1.0m)
```

See [ESRI:54030](https://epsg.io/54030).
