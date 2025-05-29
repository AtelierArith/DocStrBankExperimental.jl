```Julia
yard(U::UnitSystem) = 𝟑*foot(U)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2⋅3 = 2.36793488043(73) × 10¹²) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

English unit of `length` (m or ft).

```Julia
julia> yard(Metric) # m
ft⋅3 = 0.9144000000000001 [m] Metric

julia> yard(English) # ft
3 = 3.0 [ft] English

julia> yard(IPS) # in
2²3² = 36.0 [in] IPS
```
