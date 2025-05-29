```Julia
boltzmann(U::UnitSystem) = molargas(x)/avogadro(x)
entropy : [FLΘ⁻¹], [FLΘ⁻¹], [ML²T⁻²Θ⁻¹], [ML²T⁻²Θ⁻¹], [ML²T⁻²Θ⁻¹]
FLΘ⁻¹ [kB] 統一

ボルツマン定数 `kB` は、単位数のマイクロ状態の置換のエントロピー量です。

```

Julia julia> boltzmann(SI2019) # J⋅K⁻¹ kB = 1.380649×10⁻²³ [J⋅K⁻¹] SI2019

julia> boltzmann(Metric) # J⋅K⁻¹ kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] Metric

julia> boltzmann(SI2019)/elementarycharge(SI2019) # eV⋅K⁻¹ kB⋅𝘦⁻¹ = 8.617333262145179×10⁻⁵ [V⋅K⁻¹] SI2019

julia> boltzmann(SI2019)/planck(SI2019) # Hz⋅K⁻¹ kB⋅𝘩⁻¹ = 2.0836619123327576×10¹⁰ [Hz⋅K⁻¹] SI2019

julia> boltzmann(CGS) # erg⋅K⁻¹ kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2¹¹5¹⁰ = 1.38064899953(43) × 10⁻¹⁶ [erg⋅K⁻¹] ガウス

julia> boltzmann(SI2019)/calorie(SI2019) # calᵢₜ⋅K⁻¹ kB⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻²3⁻²5⁻¹43 = 3.2976728498006145×10⁻²⁴ [K⁻¹] SI2019

julia> boltzmann(SI2019)*°R/calorie(SI2019) # calᵢₜ⋅°R⁻¹ kB⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻²3⁻⁴43 = 1.832040472111452×10⁻²⁴ [K⁻¹] SI2019

julia> boltzmann(Brtish) # ft⋅lb⋅°R⁻¹ kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ft⁻¹lb⁻¹2⁴3⁻²5⁴ = 5.6573024638(17) × 10⁻²⁴ [lb⋅ft⋅°R⁻¹] British

julia> boltzmann(SI2019)/planck(SI2019)/lightspeed(SI2019) # m⁻¹⋅K⁻¹ kB⋅𝘩⁻¹𝘤⁻¹ = 69.50348004861274 [m⁻¹K⁻¹] SI2019

julia> avogadro(SI2019)*boltzmann(SI2019)/calorie(SI2019) # calᵢₜ⋅mol⁻¹⋅K⁻¹ kB⋅NA⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻²3⁻²5⁻¹43 = 1.9859050081929637 [K⁻¹mol⁻¹] SI2019

julia> dB(boltzmann(SI2019)) # dB(W⋅K⁻¹⋅Hz⁻¹) dB(kB) = -228.59916717321767 [dB(kg⋅m²s⁻²K⁻¹)] SI2019 ```
