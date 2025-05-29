```
GeodeticLatLonAlt(lat, lon, alt)
GeodeticLatLonAlt{Datum}(lat, lon, alt)
```

Geodetic latitude `lat ∈ [-90°,90°]` and longitude `lon ∈ [-180°,180°]` in angular units (default to degree) and altitude in length units (default to meter) with a given `Datum` (default to `WGS84Latest`).

## Examples

```julia
GeodeticLatLonAlt(45, 45, 1) # add default units
GeodeticLatLonAlt(45°, 45°, 1m) # integers are converted converted to floats
GeodeticLatLonAlt((π/4)rad, (π/4)rad) # radians are converted to degrees
GeodeticLatLonAlt(45.0°, 45.0°, 1.0km) # length quantities are converted to meters
GeodeticLatLonAlt(45.0°, 45.0°, 1.0m)
GeodeticLatLonAlt{WGS84Latest}(45.0°, 45.0°, 1.0m)
```
