```
LatLonAlt(lat, lon, alt)
LatLonAlt{Datum}(lat, lon, alt)
```

Alias to [`GeodeticLatLonAlt`](@ref).

## Examples

```julia
LatLonAlt(45, 45, 1) # add default units
LatLonAlt(45°, 45°, 1m) # integers are converted converted to floats
LatLonAlt((π/4)rad, (π/4)rad) # radians are converted to degrees
LatLonAlt(45.0°, 45.0°, 1.0km) # length quantities are converted to meters
LatLonAlt(45.0°, 45.0°, 1.0m)
LatLonAlt{WGS84Latest}(45.0°, 45.0°, 1.0m)
```
