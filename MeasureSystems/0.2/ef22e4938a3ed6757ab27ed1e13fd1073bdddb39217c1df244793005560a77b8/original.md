```Julia
abfarad(U::UnitSystem) = capacitance(𝟏,U,EMU)
capacitance : [F⁻¹L⁻¹Q²], [F⁻¹L⁻¹Q²], [M⁻¹L⁻²T²Q²], [L⁻¹T²], [L]
F⁻¹L⁻¹Q²⋅(𝘤²R∞⋅α⁻²τ²2⁴5² = 2.92472345084(90) × 10³²) [ħ⋅𝘤⁻³μ₀⁻¹mₑ⁻¹ϕ⋅λ⁻¹αL⁻²g₀] Unified
```

Electromagnetic unit of `capacitance` (F).

```Julia
julia> abfarad(Metric) # F
2⁹5⁹ = 1.0×10⁹ [F] Metric

julia> abfarad(EMU) # abF
𝟏 = 1.0 [cm⁻¹s²] EMU

julia> abfarad(ESU) # statF
𝘤²2⁴5⁴ = 8.987551787368175×10²⁰ [cm] ESU
```
