```Julia
fahrenheit(U::UnitSystem) = temperature(Constant(459.67),U,English)
temperature : [Θ], [Θ], [Θ], [Θ], [Θ]
Θ⋅459.67 [kB⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

English unit of `temperature` (K or °R).

```Julia
julia> fahrenheit(Metric) # K
3⁻²5⋅459.67 = 255.37222222222223 [K] Metric

julia> fahrenheit(SI2019) # K
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴3⁻²5⁴⋅459.67 = 255.372222134(79) [K] SI2019

julia> fahrenheit(British) # °R
459.67 = 459.67 [°R] British
```
