```Julia
熱伝導率 : [FLT⁻¹Θ⁻¹], [FLT⁻¹Θ⁻¹], [ML²T⁻³Θ⁻¹], [ML²T⁻³Θ⁻¹], [ML²T⁻³Θ⁻¹]
熱伝導率(U::UnitSystem,S::UnitSystem) = 熱伝導率(U,S)*長さ(U,S)
熱伝導率(v::Real,U::UnitSystem,S::UnitSystem) = v/熱伝導率(U,S)
FLT⁻¹Θ⁻¹ [kB⋅ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] 統一

```

`熱抵抗` (W⋅K⁻¹) の逆数、単位変換係数。

```Julia
julia> 熱伝導率(Metric,SI2019) # K⋅K⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> 熱伝導率(CGS,Metric) # W⋅s⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> 熱伝導率(English,Metric) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
g₀⋅ft⋅lb⋅3²5⁻¹ = 2.440472306996521 [J⋅K⁻¹]/[lbf⋅ft⋅°R⁻¹] English -> Metric
```
