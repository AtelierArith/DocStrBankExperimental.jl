```Julia
reluctance : [F⁻¹L⁻¹T⁻²Q²RC⁻²], [F⁻¹L⁻¹T⁻²Q²], [M⁻¹L⁻²Q²], [L⁻¹], [LT⁻²]
reluctance(U::UnitSystem,S::UnitSystem) = rationalization(U,S)*lorentz(U,S)^2/inductance(U,S)
reluctance(v::Real,U::UnitSystem,S::UnitSystem) = v/reluctance(U,S)
F⁻¹L⁻¹T⁻²Q²RC⁻² [ħ⁻¹𝘤⋅μ₀⁻¹mₑ⋅ϕ⁻¹g₀⁻¹] 統一

磁気 `reluctance` または磁気抵抗 (H⁻¹, Gb⋅Mx⁻¹)、単位換算係数。

```

Julia julia> reluctance(EMU,Metric) # abH⋅H⁻¹ τ⁻¹2⁸5⁹ = 7.957747154594767×10⁷ [F]/[cm⁻¹s²] EMU -> Metric

julia> reluctance(ESU,Metric) # statH⋅H⁻¹ 𝘤⁻²τ⁻¹2⁴5⁵ = 8.85418781762039×10⁻¹⁴ [F]/[cm] ESU -> Metric

julia> reluctance(Metric,SI2019) # H⋅H⁻¹ 𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019 ```
