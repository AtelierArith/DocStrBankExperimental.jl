```Julia
volumeflow : [L³T⁻¹], [L³T⁻¹], [L³T⁻¹], [L³T⁻¹], [L³T⁻¹]
volumeflow(U::UnitSystem,S::UnitSystem) = area(U,S)*speed(U,S)
volumeflow(v::Real,U::UnitSystem,S::UnitSystem) = v/volumeflow(U,S)
L³T⁻¹ [ħ²𝘤⁻¹mₑ⁻²ϕ²g₀²] Unified
```

Volumetric flow rate or `volumeflow` (m³⋅s⁻¹), unit conversion factor.

```Julia
julia> volumeflow(CGS,Metric) # m³⋅cm⁻³
2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [m³]/[mL] Gauss -> Metric

julia> volumeflow(English,Metric) # m³⋅ft⁻³
ft³ = 0.028316846592000004 [m³]/[ft³] English -> Metric

julia> volumeflow(Survey,English) # ft³⋅ftUS⁻³
ft⁻³ftUS³ = 1.0000060000239996 [ft³]/[ft³] Survey -> English
```
