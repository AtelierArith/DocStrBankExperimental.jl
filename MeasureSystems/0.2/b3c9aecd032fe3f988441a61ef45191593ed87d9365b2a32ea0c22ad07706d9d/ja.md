```Julia
導電率 : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
導電率(U::UnitSystem,S::UnitSystem) = 電流(U,S)/電位(U,S)
導電率(v::Real,U::UnitSystem,S::UnitSystem) = v/導電率(U,S)
F⁻¹L⁻¹T⁻¹Q² [𝘤⁻¹μ₀⁻¹λ⁻¹αL⁻²] 統一

電気的 `導電率` または `電流` あたりの `電位` (S, Ω⁻¹, A⋅V⁻¹)、単位換算係数。

```

Julia julia> 導電率(EMU,Metric) # S⋅abS⁻¹ 2⁹5⁹ = 1.0×10⁹ [F]/[cm⁻¹s²] EMU -> Metric

julia> 導電率(ESU,Metric) # S⋅statS⁻¹ 𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [F]/[cm] ESU -> Metric

julia> 導電率(Metric,SI2019) # S⋅S⁻¹ 𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019 ```
