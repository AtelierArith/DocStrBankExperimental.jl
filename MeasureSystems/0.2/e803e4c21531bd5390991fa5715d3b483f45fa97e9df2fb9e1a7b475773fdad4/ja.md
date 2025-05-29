```Julia
静電容量 : [F⁻¹L⁻¹Q²], [F⁻¹L⁻¹Q²], [M⁻¹L⁻²T²Q²], [L⁻¹T²], [L]
静電容量(U::UnitSystem,S::UnitSystem) = 電荷(U,S)/電位(U,S)
静電容量(v::Real,U::UnitSystem,S::UnitSystem) = v/静電容量(U,S)
F⁻¹L⁻¹Q² [ħ⋅𝘤⁻³μ₀⁻¹mₑ⁻¹ϕ⋅λ⁻¹αL⁻²g₀] 統一

電気的 `静電容量` または `電荷` あたりの `電位` (F, C⋅V⁻¹)、単位換算係数。

```

Julia julia> 静電容量(EMU,Metric) # F⋅abF⁻¹ 2⁹5⁹ = 1.0×10⁹ [F]/[cm⁻¹s²] EMU -> Metric

julia> 静電容量(ESU,Metric) # F⋅cm⁻¹ 𝘃⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [F]/[cm] ESU -> Metric

julia> 静電容量(Metric,SI2019) # F⋅F⁻¹ 𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019 ```
