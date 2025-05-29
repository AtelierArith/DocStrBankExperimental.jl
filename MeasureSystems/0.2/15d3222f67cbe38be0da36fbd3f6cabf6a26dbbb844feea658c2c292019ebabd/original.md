```Julia
viscosity : [FL⁻²T], [FL⁻²T], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹], [ML⁻¹T⁻¹]
viscosity(U::UnitSystem,S::UnitSystem) = inertia(U,S)/length(U,S)/time(U,S)
viscosity(v::Real,U::UnitSystem,S::UnitSystem) = v/viscosity(U,S)
FL⁻²T [ħ⁻²𝘤³mₑ³ϕ⁻²g₀⁻³] Unified
```

Resistance to deformation or `viscosity` (Pa⋅s, kg⋅m⁻¹⋅s⁻¹), unit conversion factor.

```Julia
julia> viscosity(CGS,Metric) # Pa⋅Ba⁻¹
2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] Gauss -> Metric

julia> viscosity(English,Metric) # Pa⋅ft²⋅lb⁻¹
g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lbf⋅ft⁻²] English -> Metric

julia> viscosity(British,Metric) # Pa⋅ft²⋅lb⁻¹
g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lb⋅ft⁻²] British -> Metric
```
