```
GeocentricLatLon(lat, lon)
GeocentricLatLon{Datum}(lat, lon)
```

Geocentric latitude `lat ∈ [-90°,90°]` and longitude `lon ∈ [-180°,180°]` in angular units (default to degree) with a given `Datum` (default to `WGS84`).

## Examples

```julia
GeocentricLatLon(45, 45) # add default units
GeocentricLatLon(45°, 45°) # integers are converted converted to floats
GeocentricLatLon((π/4)rad, (π/4)rad) # radians are converted to degrees
GeocentricLatLon(45.0°, 45.0°)
GeocentricLatLon{WGS84Latest}(45.0°, 45.0°)
```
