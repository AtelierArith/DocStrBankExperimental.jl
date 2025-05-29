```
GeodeticLatLon(lat, lon)
GeodeticLatLon{Datum}(lat, lon)
```

Geodetic latitude `lat ∈ [-90°,90°]` and longitude `lon ∈ [-180°,180°]` in angular units (default to degree) with a given `Datum` (default to `WGS84Latest`).

## Examples

```julia
GeodeticLatLon(45, 45) # add default units
GeodeticLatLon(45°, 45°) # integers are converted converted to floats
GeodeticLatLon((π/4)rad, (π/4)rad) # radians are converted to degrees
GeodeticLatLon(45.0°, 45.0°)
GeodeticLatLon{WGS84Latest}(45.0°, 45.0°)
```

See [EPSG:4326](https://epsg.io/4326).
