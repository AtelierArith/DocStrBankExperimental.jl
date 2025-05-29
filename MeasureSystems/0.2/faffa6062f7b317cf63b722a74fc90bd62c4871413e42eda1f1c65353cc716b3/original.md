```Julia
inch(U::UnitSystem) = length(𝟏,U,IPS)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2⁻¹3⁻¹ = 6.5775968901(20) × 10¹⁰) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

English unit of `length` (m or ft).

```Julia
julia> inch(Metric) # m
ft⋅2⁻²3⁻¹ = 0.0254 [m] Metric

julia> inch(English) # ft
2⁻²3⁻¹ = 0.08333333333333333 [ft] English

julia> inch(IPS) # in
𝟏 = 1.0 [in] IPS
```
