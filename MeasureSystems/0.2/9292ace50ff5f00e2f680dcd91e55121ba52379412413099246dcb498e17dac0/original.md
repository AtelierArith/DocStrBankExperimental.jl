```Julia
kelvin(U::UnitSystem) = temperature(𝟏,U,Metric)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅(kB⋅NA⋅𝘤⁻²μₑᵤ⁻¹2³5³ = 1.686370052070(49) × 10⁻¹⁰) [kB⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Metric unit of `temperature` (K or °R).

```Julia
julia> kelvin(Metric) # K
𝟏 = 1.0 [K] Metric

julia> kelvin(SI2019) # K
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [K] SI2019

julia> kelvin(British) # °R
3²5⁻¹ = 1.8 [°R] British
```
