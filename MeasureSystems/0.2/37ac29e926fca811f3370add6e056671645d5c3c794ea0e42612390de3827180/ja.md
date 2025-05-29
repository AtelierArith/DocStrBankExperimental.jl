```Julia
farad(U::UnitSystem) = capacitance(𝟏,U,Metric)
capacitance : [F⁻¹L⁻¹Q²], [F⁻¹L⁻¹Q²], [M⁻¹L⁻²T²Q²], [L⁻¹T²], [L]
F⁻¹L⁻¹Q²⋅(𝘃²R∞⋅α⁻²τ²2⁻⁵5⁻⁷ = 2.92472345084(90) × 10²³) [ħ⋅𝘃⁻³μ₀⁻¹mₑ⁻¹ϕ⋅λ⁻¹αL⁻²g₀] 統一

Metric unit of `capacitance` (F).

```

Julia julia> farad(Metric) # F 𝟏 = 1.0 [F] Metric

julia> farad(EMU) # abF 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [cm⁻¹s²] EMU

julia> farad(ESU) # statF 𝘃²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [cm] ESU ```
