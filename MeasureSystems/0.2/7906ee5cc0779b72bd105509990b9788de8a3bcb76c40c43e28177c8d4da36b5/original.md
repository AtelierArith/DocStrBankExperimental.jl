```Julia
volume : [L³], [L³], [L³], [L³], [L³]
volume(U::UnitSystem,S::UnitSystem) = length(U,S)^3
volume(v::Real,U::UnitSystem,S::UnitSystem) = v/volume(U,S)
L³ [ħ³𝘤⁻³mₑ⁻³ϕ³g₀³] Unified
```

Extent of three-dimensional shape or `volume` (m³), unit conversion factor.

```Julia
julia> volume(CGS,Metric) # m³⋅cm⁻³
2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [m³]/[mL] Gauss -> Metric

julia> volume(English,Metric) # m³⋅ft⁻³
ft³ = 0.028316846592000004 [m³]/[ft³] English -> Metric

julia> volume(Survey,English) # ft³⋅ftUS⁻³
ft⁻³ftUS³ = 1.0000060000239996 [ft³]/[ft³] Survey -> English
```
