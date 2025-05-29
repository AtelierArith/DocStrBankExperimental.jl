```Julia
pint(U::UnitSystem) = quart(U)/𝟐
```

英語の `volume` 単位 (m³ または ft³)。

```Julia
julia> pint(Metric) # m³
0.00047317647300000024

julia> pint(CGS) # cm³
473.1764730000003

julia> pint(IPS) # in³
28.875
```
