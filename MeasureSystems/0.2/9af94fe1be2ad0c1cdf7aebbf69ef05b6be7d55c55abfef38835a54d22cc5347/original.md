```Julia
earthcalorie(U::UnitSystem) = calorie(U)*(sqrt(g₀/GME)/τ)^3*𝟐^27*𝟓^21
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²g₀⁻³ᐟ²Ωᵢₜ⁻¹Vᵢₜ²GME³ᐟ²τ³2⁻²⁶3²5⁻²⁰43⁻¹ = 5.136065976(16) × 10¹³) [𝘤²mₑ⋅g₀⁻¹] Unified
```

Heat energy required to raise 1 `earthgram` of water by 1 `kelvin` in `Meridian` units.

```Julia
julia> earthcalorie(Meridian) # J
g₀⋅Ωᵢₜ⁻¹Vᵢₜ²GME⁻¹τ⁻²2²⁰3²5¹⁵43⁻¹ = 4.1746383635(84) [eJ] Meridian

julia> earthcalorie(Metric) # J
g₀⁻³ᐟ²Ωᵢₜ⁻¹Vᵢₜ²GME³ᐟ²τ³2⁻²⁵3²5⁻²⁰43⁻¹ = 4.204951542(13) [J] Metric

julia> earthcalorie(British) # ft⋅lb
g₀⁻⁵ᐟ²ft⁻¹lb⁻¹Ωᵢₜ⁻¹Vᵢₜ²GME³ᐟ²τ³2⁻²⁵3²5⁻²⁰43⁻¹ = 3.1014130969(93) [lb⋅ft] British
```
