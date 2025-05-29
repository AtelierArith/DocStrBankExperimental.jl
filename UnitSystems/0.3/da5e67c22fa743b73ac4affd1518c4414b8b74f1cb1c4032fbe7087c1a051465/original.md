```Julia
gravitation(U::UnitSystem) = lightspeed(U)*planckreduced(U)/planckmass(U)^2
```

Universal gravitational constant `G` of Newton's law (m³⋅kg⁻¹⋅s⁻² or ft³⋅slug⁻¹⋅s⁻²).

```Julia
juila> gravitation(Metric) # m³⋅kg⁻¹⋅s⁻²
6.674302101972535e-11

julia> gravitation(English) # ft³⋅lbm⁻¹⋅s⁻²
3.322928526687524e-11

julia> gravitation(PlanckGauss)
1.0
```
