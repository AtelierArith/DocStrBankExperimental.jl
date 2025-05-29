```Julia
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
temperature(U::UnitSystem,S::UnitSystem) = mass(U,S)*speed(U,S)^2/entropy(U,S)
temperature(v::Real,U::UnitSystem,S::UnitSystem) = v/temperature(U,S)
Θ [kB⁻¹𝘤²mₑ⋅g₀⁻¹] 統一

熱力学エネルギーまたは `temperature` (K) の測定スケール、単位換算係数。

```

Julia julia> temperature(Metric,SI2019) # K⋅K⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [K]/[K] Metric -> SI2019

julia> temperature(English,SI2019) # K⋅°R⁻¹ NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴3⁻²5⁴ = 0.55555555536(17) [K]/[°R] English -> SI2019

julia> temperature(English,Metric) # K⋅°R⁻¹ 3⁻²5 = 0.5555555555555556 [K]/[°R] English -> Metric

julia> temperature(PlanckGauss,Metric) # K⋅TP⁻¹ kB⁻¹NA⁻¹𝘩⁻¹𝘤³R∞⁻¹α²μₑᵤ⋅mP⋅2⁻⁴5⁻³ = 1.416784(16) × 10³² [K]/[mP] PlanckGauss -> Metric ```
