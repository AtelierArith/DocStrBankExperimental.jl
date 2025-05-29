```
dms2ha(degrees, arcmin, arcsec)
dms2ha(parts)
dms2ha(input::AbstractString)
```

Convert (degrees, arcminutes, arcseconds) tuple to hour angles. If a string is given, will parse with [`parse_dms`](@ref) first. If an angle is input will treat as a no-op.
