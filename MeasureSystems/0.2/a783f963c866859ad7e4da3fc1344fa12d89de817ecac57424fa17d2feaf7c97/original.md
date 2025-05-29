```Julia
sealevel(U::UnitSystem) = temperature(T₀+𝟑*𝟓,U)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅288.15 [kB⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Standard `temperature` reference at `sealevel` (K or °R).

```Julia
julia> sealevel(Metric) # K
288.15 = 288.15 [K] Metric

julia> sealevel(SI2019) # K
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³⋅288.15 = 288.149999901(89) [K] SI2019

julia> sealevel(English) # °R
3²5⁻¹⋅288.15 = 518.67 [°R] English
```
