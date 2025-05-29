```
ESRIWellKnownText <: AbstractWellKnownText

ESRIWellKnownText(x::String)
ESRIWellKnownText(::CRS, x::String)
ESRIWellKnownText(::Geom, x::String)
```

Wrapper for Well-known text strings, following the ESRI standard.

These may hold CRS or geometry data. The default mode is `Unknown`, and conversions to either type will be attempted where possible. A specific type can be specified if it is known, e.g:

```julia
crs = ESRIWellKnownText(CRS(), crs_string)
```
