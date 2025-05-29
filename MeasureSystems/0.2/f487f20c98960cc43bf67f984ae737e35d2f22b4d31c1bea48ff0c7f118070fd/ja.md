```Julia
抵抗 : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
抵抗(U::UnitSystem,S::UnitSystem) = 電位(U,S)/電流(U,S)
抵抗(v::Real,U::UnitSystem,S::UnitSystem) = v/抵抗(U,S)
FLTQ⁻² [𝘃⋅μ₀⋅λ⋅αL²] 統一

電気的 `抵抗` または `電位` あたりの `電流` (Ω, S⁻¹, V⋅A⁻¹)、単位換算係数。

```

Julia julia> 抵抗(EMU,Metric) # Ω⋅abΩ⁻¹ 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> 抵抗(ESU,Metric) # Ω⋅statΩ⁻¹ 𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> 抵抗(Metric,SI2019) # Ω⋅Ω⁻¹ 𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019 ```
