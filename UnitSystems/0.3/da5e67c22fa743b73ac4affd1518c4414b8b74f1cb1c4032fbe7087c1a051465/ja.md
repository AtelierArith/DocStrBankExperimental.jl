```Julia
gravitation(U::UnitSystem) = lightspeed(U)*planckreduced(U)/planckmass(U)^2
```

ニュートンの法則の普遍的重力定数 `G` (m³⋅kg⁻¹⋅s⁻² または ft³⋅slug⁻¹⋅s⁻²)。

```Julia
juila> gravitation(Metric) # m³⋅kg⁻¹⋅s⁻²
6.674302101972535e-11

julia> gravitation(English) # ft³⋅lbm⁻¹⋅s⁻²
3.322928526687524e-11

julia> gravitation(PlanckGauss)
1.0
```
