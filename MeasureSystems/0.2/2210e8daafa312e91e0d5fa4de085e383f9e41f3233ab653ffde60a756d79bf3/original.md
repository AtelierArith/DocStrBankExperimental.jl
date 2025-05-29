```Julia
barn(U::UnitSystem) = area((𝟐*𝟓)^-28,U,Metric)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴τ²2⁻²⁶5⁻²⁸ = 0.00067060544436(41)) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

Unit of `area` defined by `100` square femto-meters (m² or ft²).

```Julia
julia> barn(Metric) # m²
2⁻²⁸5⁻²⁸ = 1.0×10⁻²⁸ [m²] Metric

julia> barn(CGS) # cm²
2⁻²⁴5⁻²⁴ = 1.0×10⁻²⁴ [cm²] Gauss

julia> barn(English) # ft²
ft⁻²2⁻²⁸5⁻²⁸ = 1.076391041670972×10⁻²⁷ [ft²] English
```
