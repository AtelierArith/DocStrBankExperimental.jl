```Julia
henry(U::UnitSystem) = inductance(𝟏,U,Metric)
inductance : [FLT²Q⁻²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
FLT²Q⁻²⋅(R∞⋅α⁻²2⁷5⁷ = 2.06074224158(63) × 10¹⁸) [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] Unified
```

Metric unit of `inductance` (H).

```Julia
julia> henry(Metric) # H
𝟏 = 1.0 [H] Metric

julia> henry(EMU) # abH
2⁹5⁹ = 1.0×10⁹ [cm] EMU

julia> henry(ESU) # statH
𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [cm⁻¹s²] ESU
```
