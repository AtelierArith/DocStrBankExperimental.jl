```
WellKnownText <: AbstractWellKnownText

WellKnownText(val)
WellKnownText(mode, val)
```

Wrapper for Well-known text (WKT) v1, following the OGC standard. These may hold CRS or geometry data.

These may hold CRS or geometry data. The default mode is `Mixed()`, and conversions to either type will be attempted where possible. A specific type can be specified if it is known, e.g.:

```julia
geom = WellKnownText(Geom(), geom_string)
```
