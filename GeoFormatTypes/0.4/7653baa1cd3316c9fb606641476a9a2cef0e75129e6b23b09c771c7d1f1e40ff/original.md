```
WellKnownText2 <: AbstractWellKnownText

WellKnownText2(val)
WellKnownText2(mode, val)
```

Wrapper for Well-known text v2 objects, following the new OGC standard.

These may hold CRS or geometry data. The default mode is `Unknown()`, and conversions to either type will be attempted where possible. A specific type can be specified if it is known, e.g.:

```julia
crs = WellKnownText2(CRS(), crs_string)
```
