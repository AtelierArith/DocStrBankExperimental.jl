```Julia
cup(U::UnitSystem) = pint(U)/𝟐
```

英語の `volume` 単位 (m³ または ft³)。

```Julia
julia> cup(Metric) # m³
0.00023658823650000012

julia> cup(CGS) # cm³
236.58823650000016

julia> cup(IPS) # in³
14.4375
```
