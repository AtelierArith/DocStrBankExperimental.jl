```Julia
statfarad(U::UnitSystem) = capacitance(𝟏,U,ESU)
capacitance : [F⁻¹L⁻¹Q²], [F⁻¹L⁻¹Q²], [M⁻¹L⁻²T²Q²], [L⁻¹T²], [L]
F⁻¹L⁻¹Q²⋅(R∞⋅α⁻²τ²5⁻² = 3.25419371152(10) × 10¹¹) [ħ⋅𝘤⁻³μ₀⁻¹mₑ⁻¹ϕ⋅λ⁻¹αL⁻²g₀] 統一

静電単位の `capacitance` (F)。

```

Julia julia> statfarad(Metric) # F 𝘃⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [F] メトリック

julia> statfarad(EMU) # abF 𝘃⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻¹s²] EMU

julia> statfarad(ESU) # statF 𝟏 = 1.0 [cm] ESU ```
