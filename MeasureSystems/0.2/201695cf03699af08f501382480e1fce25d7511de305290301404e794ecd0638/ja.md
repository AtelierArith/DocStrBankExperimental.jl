```Julia
rankine(U::UnitSystem) = temperature(𝟏,U,English)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅(kB⋅NA⋅𝘤⁻²μₑᵤ⁻¹2³3⁻²5⁴ = 9.36872251150(27) × 10⁻¹¹) [kB⁻¹𝘤²mₑ⋅g₀⁻¹] 統一

English unit of `temperature` (K or °R).

```

Julia julia> rankine(Metric) # K 3⁻²5 = 0.5555555555555556 [K] メトリック

julia> rankine(SI2019) # K NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴3⁻²5⁴ = 0.55555555536(17) [K] SI2019

julia> rankine(British) # °R 𝟏 = 1.0 [°R] ブリティッシュ ```
