```Julia
fluidounce(U::UnitSystem) = cup(U)/𝟐^3
```

English unit of `volume` (m³ or ft³).

```Julia
julia> fluidounce(Metric) # m³
2.9573529562500015e-5

julia> fluidounce(CGS) # cm³
29.57352956250002

julia> fluidounce(IPS) # in³
1.8046875
```
