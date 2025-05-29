```Julia
thermalconductivity : [FT⁻¹Θ⁻¹], [FT⁻¹Θ⁻¹], [MLT⁻³Θ⁻¹], [MLT⁻³Θ⁻¹], [MLT⁻³Θ⁻¹]
thermalconductivity(U::UnitSystem,S::UnitSystem) = force(U,S)/time(U,S)/temperature(U,S)
thermalconductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalconductivity(U,S)
FT⁻¹Θ⁻¹ [kB⋅ħ⁻²𝘤³mₑ²ϕ⁻²g₀⁻²] 統一

熱伝導率または `thermalconductivity` (W⋅m⁻¹⋅K⁻¹)、単位変換係数。

```

Julia julia> thermalconductivity(Metric,SI2019) # K⋅K⁻¹ NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> thermalconductivity(CGS,Metric) # N⋅dyn⁻¹ 2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [N]/[dyn] Gauss -> Metric

julia> thermalconductivity(English,Metric) # N⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹ g₀⋅lb⋅3²5⁻¹ = 8.0067989074689 [kg⋅m⋅s⁻²K⁻¹]/[lbf⋅°R⁻¹] English -> Metric ```
