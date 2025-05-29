```
dms2deg(degrees, arcmin, arcsec)
dms2deg(parts)
dms2deg(input::AbstractString)
```

Convert (degrees, arcminutes, arcseconds) tuple to degrees. If a string is given, will parse with [`parse_dms`](@ref) first. If an angle is input will treat as a no-op.
