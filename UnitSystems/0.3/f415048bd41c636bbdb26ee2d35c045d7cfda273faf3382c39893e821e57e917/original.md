```Julia
cup(U::UnitSystem) = pint(U)/𝟐
```

English unit of `volume` (m³ or ft³).

```Julia
julia> cup(Metric) # m³
0.00023658823650000012

julia> cup(CGS) # cm³
236.58823650000016

julia> cup(IPS) # in³
14.4375
```
