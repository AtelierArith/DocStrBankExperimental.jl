```
dms2rad(degrees, arcmin, arcsec)
dms2rad(parts)
dms2rad(input::AbstractString)
```

Convert (degrees, arcminutes, arcseconds) tuple to radians. If a string is given, will parse with [`parse_dms`](@ref) first. If an angle is input will treat as a no-op.
