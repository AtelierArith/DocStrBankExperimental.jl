```Julia
hectare(U::UnitSystem) = area(hecto^2,U,Metric)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴τ²2⁶5⁴ = 6.7060544436(41) × 10²⁸) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] Unified
```

Metric unit of land `area` defined by `100` square meters (m² or ft²).

```Julia
julia> hectare(Metric) # m²
2⁴5⁴ = 10000.0 [m²] Metric

julia> hectare(English) # ft²
ft⁻²2⁴5⁴ = 107639.1041670972 [ft²] English

julia> hectare(Survey) # ftUS²
ftUS⁻²2⁴5⁴ = 107638.67361111114 [ft²] Survey
```
