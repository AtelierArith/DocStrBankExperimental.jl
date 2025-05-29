```
WebMercator(x, y)
WebMercator{Datum}(x, y)
```

Web Mercator coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
WebMercator(1, 1) # add default units
WebMercator(1m, 1m) # integers are converted converted to floats
WebMercator(1.0km, 1.0km) # length quantities are converted to meters
WebMercator(1.0m, 1.0m)
WebMercator{WGS84Latest}(1.0m, 1.0m)
```

See [EPSG:3857](https://epsg.io/3857).
