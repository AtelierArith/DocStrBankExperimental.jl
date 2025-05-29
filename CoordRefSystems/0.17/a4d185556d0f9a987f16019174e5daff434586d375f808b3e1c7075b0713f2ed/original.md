```
AuthalicLatLon(lat, lon)
AuthalicLatLon{Datum}(lat, lon)
```

Authalic latitude `lat ∈ [-90°,90°]` and longitude `lon ∈ [-180°,180°]` in angular units (default to degree) with a given `Datum` (default to `WGS84`).

## Examples

```julia
AuthalicLatLon(45, 45) # add default units
AuthalicLatLon(45°, 45°) # integers are converted converted to floats
AuthalicLatLon((π/4)rad, (π/4)rad) # radians are converted to degrees
AuthalicLatLon(45.0°, 45.0°)
AuthalicLatLon{WGS84Latest}(45.0°, 45.0°)
```
