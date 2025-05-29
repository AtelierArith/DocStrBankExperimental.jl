```Julia
mile(U::UnitSystem) = length(𝟏,U,MPH)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2⁶3⋅5⋅11 = 4.1675653896(13) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

Statute `English` mile (m or ft).

```Julia
julia> mile(Metric) # m
ft⋅2⁵3⋅5⋅11 = 1609.344 [m] Metric

julia> mile(English) # ft
2⁵3⋅5⋅11 = 5280.0 [ft] English

julia> mile(Nautical) # nm
ft⋅ftUS⁻¹2⁵3⋅5⋅11 = 5279.989440000001 [ft] Survey
```
