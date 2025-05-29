```Julia
抵抗率 : [FL²TQ⁻²], [FL²TQ⁻²], [ML³T⁻¹Q⁻²], [L²T⁻¹], [T]
抵抗率(U::UnitSystem,S::UnitSystem) = 抵抗(U,S)*長さ(U,S)
抵抗率(v::Real,U::UnitSystem,S::UnitSystem) = v/抵抗率(U,S)
FL²TQ⁻² [ħ⋅μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] 統一

電気的 `抵抗率` または `抵抗` による `長さ` (Ω⋅m)、単位換算係数。

```

Julia julia> 抵抗(EMU,Metric) # Ω⋅m⋅abΩ⁻¹⋅cm⁻¹ 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> 抵抗(ESU,Metric) # Ω⋅m⋅statΩ⁻¹⋅cm⁻¹ 𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> 抵抗(Metric,SI2019) # Ω⋅Ω⁻¹ 𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019 ```
