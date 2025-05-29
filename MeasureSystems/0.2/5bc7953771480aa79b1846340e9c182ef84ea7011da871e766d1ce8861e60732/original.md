```Julia
celsius(U::UnitSystem) = temperature(T₀,U,Metric)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅(kB⋅NA⋅𝘤⁻²μₑᵤ⁻¹T₀⋅2³5³ = 4.60631979723(13) × 10⁻⁸) [kB⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Metric unit of `temperature` (K or °R).

```Julia
julia> celsius(Metric) # K
T₀ = 273.15 [K] Metric

julia> celsius(SI2019) # K
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹T₀⋅2⁴5³ = 273.149999906(84) [K] SI2019

julia> celsius(British) # °R
T₀⋅3²5⁻¹ = 491.66999999999996 [°R] British
```
