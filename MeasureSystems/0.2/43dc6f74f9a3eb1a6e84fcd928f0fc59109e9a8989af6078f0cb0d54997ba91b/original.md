```Julia
diffusivity : [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹], [L²T⁻¹]
diffusivity(U::UnitSystem,S::UnitSystem) = speed(U,S)*length(U,S)
diffusivity(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusivity(U,S)
L²T⁻¹ [ħ⋅mₑ⁻¹ϕ⋅g₀] Unified
```

Thermal `diffusivity` or kinematic viscostiy (m²⋅s⁻¹), unit conversion factor.

```Julia
julia> diffusivity(CGS,Metric) # m²⋅cm⁻²
2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] Gauss -> Metric

julia> diffusivity(English,Metric) # m²⋅ft⁻²
ft² = 0.09290304 [m²]/[ft²] English -> Metric

julia> diffusivity(Survey,English) # ft²⋅ftUS⁻²
ft⁻²ftUS² = 1.0000040000119996 [ft²]/[ft²] Survey -> English
```
