```Julia
area : [L²], [L²], [L²], [L²], [L²]
area(U::UnitSystem,S::UnitSystem) = length(U,S)^2
area(v::Real,U::UnitSystem,S::UnitSystem) = v/area(U,S)
L² [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

Extent of two-dimensional shape or `area` (m²), unit conversion factor.

```Julia
julia> area(CGS,Metric) # m²⋅cm⁻²
2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] Gauss -> Metric

julia> area(English,Metric) # m²⋅ft⁻²
ft² = 0.09290304 [m²]/[ft²] English -> Metric

julia> area(Survey,English) # ft²⋅ftUS⁻²
ft⁻²ftUS² = 1.0000040000119996 [ft²]/[ft²] Survey -> English
```
