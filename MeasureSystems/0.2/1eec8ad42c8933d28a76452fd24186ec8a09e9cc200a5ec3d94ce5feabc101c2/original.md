```Julia
thermalconductance : [FLT⁻¹Θ⁻¹], [FLT⁻¹Θ⁻¹], [ML²T⁻³Θ⁻¹], [ML²T⁻³Θ⁻¹], [ML²T⁻³Θ⁻¹]
thermalconductance(U::UnitSystem,S::UnitSystem) = thermalconductivity(U,S)*length(U,S)
thermalconductance(v::Real,U::UnitSystem,S::UnitSystem) = v/thermalconductance(U,S)
FLT⁻¹Θ⁻¹ [kB⋅ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Reciprocal of `thermalresistance` (W⋅K⁻¹), unit conversion factor.

```Julia
julia> thermalconductance(Metric,SI2019) # K⋅K⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [K⁻¹]/[K⁻¹] Metric -> SI2019

julia> thermalconductance(CGS,Metric) # W⋅s⋅erg⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J]/[erg] Gauss -> Metric

julia> thermalconductance(English,Metric) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
g₀⋅ft⋅lb⋅3²5⁻¹ = 2.440472306996521 [J⋅K⁻¹]/[lbf⋅ft⋅°R⁻¹] English -> Metric
```
