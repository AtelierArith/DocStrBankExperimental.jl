```Julia
電気分極率 : [F⁻¹LQ²], [F⁻¹LQ²], [M⁻¹T²Q²], [LT²], [L³]
電気分極率(U::UnitSystem,S::UnitSystem) = 電気双極子モーメント(U,S)/電場(U,S)
電気分極率(v::Real,U::UnitSystem,S::UnitSystem) = v/電気分極率(U,S)
F⁻¹LQ² [ħ³𝘤⁻⁵μ₀⁻¹mₑ⁻³ϕ³λ⁻¹αL⁻²g₀³] 統一

```

分極率または `電気双極子モーメント` あたり `電場` (C⋅m²⋅V⁻¹)、単位換算係数。

```Julia
julia> 電気分極率(EMU,Metric) # C⋅m²⋅abV⋅abC⁻¹⋅cm⁻²⋅V⁻¹
2⁵5⁵ = 100000.0 [kg⁻¹s²C²]/[cm⋅s²] EMU -> Metric

julia> 電気分極率(ESU,Metric) # C⋅m²⋅statV⋅statC⁻¹⋅cm⁼²⋅V⁻¹
𝘤⁻²2⋅5 = 1.1126500560536184×10⁻¹⁶ [kg⁻¹s²C²]/[mL] ESU -> Metric

julia> 電気分極率(Metric,Gauss) # D⋅cm²⋅V⁻¹⋅C⁻¹⋅m⁻²⋅abV⁻¹
𝘤²2⁻¹5⁻¹ = 8.987551787368176×10¹⁵ [mL]/[kg⁻¹s²C²] Metric -> Gauss

julia> 電気分極率(Metric,SI2019) # C⋅V⋅C⁻¹⋅V⁻¹
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
