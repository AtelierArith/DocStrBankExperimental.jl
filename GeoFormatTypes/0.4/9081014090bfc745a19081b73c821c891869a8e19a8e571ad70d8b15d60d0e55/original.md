```
WellKnownBinary <: MixedFormat
```

Wrapper for Well-known binary (WKB) objects.

These may hold CRS or geometry data. The default mode is `Unknown`, and conversions to either type will be attempted where possible. A specific type can be specified if it is known, e.g:

```julia
crs = WellKnownBinary(CRS(), crs_blob)
```
