```
PlateCarree(x, y)
PlateCarree{Datum}(x, y)
```

Plate Carrée coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
PlateCarree(1, 1) # add default units
PlateCarree(1m, 1m) # integers are converted converted to floats
PlateCarree(1.0km, 1.0km) # length quantities are converted to meters
PlateCarree(1.0m, 1.0m)
PlateCarree{WGS84Latest}(1.0m, 1.0m)
```

See [EPSG:32662](https://epsg.io/32662).
