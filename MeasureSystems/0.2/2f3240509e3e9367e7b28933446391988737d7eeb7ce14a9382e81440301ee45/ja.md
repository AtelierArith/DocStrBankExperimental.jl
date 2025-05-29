```Julia
インダクタンス : [FLT²Q⁻²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
インダクタンス(U::UnitSystem,S::UnitSystem) = 磁束(U,S)/電流(U,S)
インダクタンス(v::Real,U::UnitSystem,S::UnitSystem) = v/インダクタンス(U,S)
FLT²Q⁻² [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] 統一

電磁`磁束`あたりの`電流`または`インダクタンス` (H, Ω⋅s, Wb⋅A⁻¹)、単位変換係数。

```

Julia julia> インダクタンス(EMU,Metric) # H⋅abH⁻¹ 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> インダクタンス(ESU,Metric) # H⋅statH⁻¹ 𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> インダクタンス(Metric,SI2019) # H⋅H⁻¹ 𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019 ```
