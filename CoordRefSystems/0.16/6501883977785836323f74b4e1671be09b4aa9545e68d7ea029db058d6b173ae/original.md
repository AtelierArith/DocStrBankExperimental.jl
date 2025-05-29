```
LatLon(lat, lon)
LatLon{Datum}(lat, lon)
```

Alias to [`GeodeticLatLon`](@ref).

## Examples

```julia
LatLon(45, 45) # add default units
LatLon(45°, 45°) # integers are converted converted to floats
LatLon((π/4)rad, (π/4)rad) # radians are converted to degrees
LatLon(45.0°, 45.0°)
LatLon{WGS84Latest}(45.0°, 45.0°)
```

See [EPSG:4326](https://epsg.io/4326).
