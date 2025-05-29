```Julia
barn(U::UnitSystem) = area((𝟐*𝟓)^-28,U,Metric)
```

Unit of `area` defined by `100` square femto-meters (m² or ft²).

```Julia
julia> barn(Metric) # m²
1.0000000000000015e-28

julia> barn(CGS) # cm²
1.000000000000001e-24

julia> barn(English) # ft²
1.0763910416709738e-27
```
