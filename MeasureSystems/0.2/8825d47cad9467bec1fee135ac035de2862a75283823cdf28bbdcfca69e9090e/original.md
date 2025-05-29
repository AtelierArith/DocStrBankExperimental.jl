```Julia
angulararea : [L²A⁻²], [L²], [L²], [L²], [L²]
angulararea(U::UnitSystem,S::UnitSystem) = area(U,S)/solidangle(U,S)
angulararea(v::Real,U::UnitSystem,S::UnitSystem) = v/angulararea(U,S)
L²A⁻² [ħ²𝘤⁻²mₑ⁻²g₀²] Unified
```

Extent of two-dimensional shape or `area` (m²), unit conversion factor.

```Julia
julia> angulararea(CGS,Metric) # m²⋅cm⁻²
2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] Gauss -> Metric

julia> angulararea(English,Metric) # m²⋅ft⁻²
ft² = 0.09290304 [m²]/[ft²] English -> Metric
```
