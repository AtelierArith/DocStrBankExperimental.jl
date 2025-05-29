```Julia
quart(U::UnitSystem) = gallon(U)/𝟐^2
```

英語の`volume`（m³またはft³）。

```Julia
julia> quart(Metric) # m³
0.0009463529460000005

julia> quart(CGS) # cm³
946.3529460000007

julia> quart(IPS) # in³
57.75
```
