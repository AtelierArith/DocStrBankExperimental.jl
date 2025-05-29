```Julia
admiraltymile(U::UnitSystem) = length(𝟐^6*𝟓*𝟏𝟗,U,English)
```

Historic nautical mile as defined by the Clarke authalic radius (m or ft).

```Julia
julia> admiraltymile(Metric) # m
1853.1840000000002

julia> admiraltymile(English) # ft
6080

julia> admiraltymile(Nautical) # nm
0.9992723593592421
```
