```Julia
透過率 : [FT²Q⁻²R⁻¹C²], [FT²Q⁻²], [MLQ⁻²], [𝟙], [L⁻²T²]
透過率(U::UnitSystem,S::UnitSystem) = 透過率(S)/透過率(U)
透過率(v::Real,U::UnitSystem,S::UnitSystem) = v/透過率(U,S)
FT²Q⁻²R⁻¹C² [μ₀] 統一

```

磁気 `透過率` または `インダクタンス` あたりの `長さ` (H⋅m⁻¹)、単位変換係数。

```Julia
julia> 透過率(EMU,Metric) # H⋅cm⋅abH⁻¹⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [kg⋅m⋅s⁻²C⁻²]/[gal⋅cm⁻¹] EMU -> Metric

julia> 透過率(ESU,Metric) # H⋅cm⋅statH⁻¹⋅m⁼¹
𝘤²τ⋅2⁻²5⁻³ = 1.129409066758147×10¹⁵ [kg⋅m⋅s⁻²C⁻²]/[cm⁻²] ESU -> Metric

julia> 透過率(Metric,SI2019) # H⋅H⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
