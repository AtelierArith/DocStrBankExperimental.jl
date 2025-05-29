```
EqualEarth(x, y)
EqualEarth{Datum}(x, y)
```

Equal Earth coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
EqualEarth(1, 1) # add default units
EqualEarth(1m, 1m) # integers are converted converted to floats
EqualEarth(1.0km, 1.0km) # length quantities are converted to meters
EqualEarth(1.0m, 1.0m)
EqualEarth{WGS84Latest}(1.0m, 1.0m)
```

See [Equal Earth projection](https://equal-earth.com/equal-earth-projection.html).
