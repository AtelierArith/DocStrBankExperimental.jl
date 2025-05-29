```Julia
etendue : [L²A²], [L²], [L²], [L²], [L²]
etendue(U::UnitSystem,S::UnitSystem) = area(U,S)*solidangle(U,S)
etendue(v::Real,U::UnitSystem,S::UnitSystem) = v/etendue(U,S)
L²A² [ħ²𝘤⁻²mₑ⁻²ϕ⁴g₀²] Unified
```

Etendue or `area` times `solidangle` (m², ft²), unit conversion factor.

```Julia
julia> etendue(CGS,Metric) # m²⋅cm⁻²
2⁻⁴5⁻⁴ = 0.0001 [m²]/[cm²] Gauss -> Metric

julia> etendue(English,Metric) # m²⋅ft⁻²
ft² = 0.09290304 [m²]/[ft²] English -> Metric
```
