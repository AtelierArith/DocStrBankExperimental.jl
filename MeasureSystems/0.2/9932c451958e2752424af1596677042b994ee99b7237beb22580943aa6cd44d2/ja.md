```Julia
stathenry(U::UnitSystem) = inductance(𝟏,U,ESU)
inductance : [FLT²Q⁻²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
FLT²Q⁻²⋅(𝘤²R∞⋅α⁻²2²5² = 1.85210276166(57) × 10³⁰) [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] 統一

静電単位の `inductance` (H)。

```

Julia julia> stathenry(Metric) # H 𝘃²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [H] メトリック

julia> stathenry(EMU) # abH 𝘃²2⁴5⁴ = 8.987551787368175×10²⁰ [cm] EMU

julia> stathenry(ESU) # statH 𝟏 = 1.0 [cm⁻¹s²] ESU ```
