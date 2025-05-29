```
WinkelTripel(x, y)
WinkelTripel{Datum}(x, y)
```

Winkel Tripel coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
WinkelTripel(1, 1) # add default units
WinkelTripel(1m, 1m) # integers are converted converted to floats
WinkelTripel(1.0km, 1.0km) # length quantities are converted to meters
WinkelTripel(1.0m, 1.0m)
WinkelTripel{WGS84Latest}(1.0m, 1.0m)
```

See [ESRI:54042](https://epsg.io/54042).
