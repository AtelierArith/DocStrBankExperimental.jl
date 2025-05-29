```Julia
エントロピー : [FLΘ⁻¹], [FLΘ⁻¹], [ML²T⁻²Θ⁻¹], [ML²T⁻²Θ⁻¹], [ML²T⁻²Θ⁻¹]
entropy(U::UnitSystem,S::UnitSystem) = energy(U,S)/temperature(U,S)
entropy(v::Real,U::UnitSystem,S::UnitSystem) = v/entropy(U,S)
FLΘ⁻¹ [kB] 統一

熱容量または `エネルギー` あたりの `温度` または `エントロピー` (J⋅K⁻¹)、単位換算係数。

```

Julia julia> entropy(Metric,SI2019) # K⋅K⁻¹ NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> entropy(CGS,Metric) # J⋅erg⁻¹ 2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> entropy(English,SI2019) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹ NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅g₀⋅ft⋅lb⋅2⁻⁴3²5⁻⁴ = 2.44047230784(75) [J⋅K⁻¹]/[lbf⋅ft⋅°R⁻¹] English -> SI2019

julia> entropy(Survey,English) # ftUS²⋅°R⋅°ft⁻²⋅°R⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English ```
