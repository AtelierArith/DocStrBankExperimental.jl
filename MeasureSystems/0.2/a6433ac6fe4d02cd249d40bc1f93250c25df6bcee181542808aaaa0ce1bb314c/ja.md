```Julia
透過率 : [FLT²Q⁻²R⁻¹C²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
透過率(U::UnitSystem,S::UnitSystem) = 1/抵抗(U,S)
透過率(v::Real,U::UnitSystem,S::UnitSystem) = v/透過率(U,S)
FLT²Q⁻²R⁻¹C² [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅g₀] 統一

磁気の`透過率`または磁気導電率 (H, Mx⋅Gb⁻¹)、単位換算係数。

```

Julia julia> 透過率(EMU,Metric) # abH⋅H⁻¹ τ⋅2⁻⁸5⁻⁹ = 1.2566370614359173×10⁻⁸ [F⁻¹]/[gal] EMU -> Metric

julia> 透過率(ESU,Metric) # statH⋅H⁻¹ 𝘤²τ⋅2⁻⁴5⁻⁵ = 1.129409066758147×10¹³ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> 透過率(Metric,SI2019) # H⋅H⁻¹ 𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019 ```
