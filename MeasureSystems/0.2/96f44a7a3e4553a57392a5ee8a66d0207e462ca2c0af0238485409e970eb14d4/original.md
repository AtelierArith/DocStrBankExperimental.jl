```Julia
thermalexpansion : [Θ⁻¹], [Θ⁻¹], [Θ⁻¹], [Θ⁻¹], [Θ⁻¹]
thermalexpansion(U::UnitSystem,S::UnitSystem) = 1/temperature(U,S)
thermalexpansion(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalexpansion(U,S)
Θ⁻¹ [kB⋅𝘤⁻²mₑ⁻¹g₀] Unified
```

Measurement scale for coefficient of `thermalexpansion` (K⁻¹), unit conversion factor.

```Julia
julia> thermalexpansion(Metric,SI2019) # K⋅K⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> thermalexpansion(English,SI2019) # °R⋅K⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴3²5⁻⁴ = 1.80000000062(55) [K⁻¹]/[°R⁻¹] English -> SI2019

julia> thermalexpansion(English,Metric) # °R⋅K⁻¹
3²5⁻¹ = 1.8 [K⁻¹]/[°R⁻¹] English -> Metric
```
