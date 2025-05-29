```
GallPeters(x, y)
GallPeters{Datum}(x, y)
```

Gall-Peters coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
GallPeters(1, 1) # add default units
GallPeters(1m, 1m) # integers are converted converted to floats
GallPeters(1.0km, 1.0km) # length quantities are converted to meters
GallPeters(1.0m, 1.0m)
GallPeters{WGS84Latest}(1.0m, 1.0m)
```
