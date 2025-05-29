```Julia
abhenry(U::UnitSystem) = inductance(𝟏,U,EMU)
inductance : [FLT²Q⁻²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
FLT²Q⁻²⋅(R∞⋅α⁻²2⁻²5⁻² = 2.06074224158(63) × 10⁹) [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] 統一

電磁単位の `inductance` (H)。

```

Julia julia> abhenry(Metric) # H 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [H] メトリック

julia> abhenry(EMU) # abH 𝟏 = 1.0 [cm] EMU

julia> abhenry(ESU) # statH 𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻¹s²] ESU ```
