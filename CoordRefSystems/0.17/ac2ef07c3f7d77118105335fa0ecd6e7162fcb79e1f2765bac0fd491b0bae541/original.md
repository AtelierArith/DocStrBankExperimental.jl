```
Sinusoidal(x, y)
Sinusoidal{Datum}(x, y)
```

Sinusoidal (Sanson-Flamsteed) coordinates in length units (default to meter) with a given `Datum` (default to `WGS84`).

## Examples

```julia
Sinusoidal(1, 1) # add default units
Sinusoidal(1m, 1m) # integers are converted converted to floats
Sinusoidal(1.0km, 1.0km) # length quantities are converted to meters
Sinusoidal(1.0m, 1.0m)
Sinusoidal{WGS84Latest}(1.0m, 1.0m)
```

See [Sinusoidal projection](https://en.wikipedia.org/wiki/Sinusoidal_projection)
