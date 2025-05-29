```Julia
kilocalorie(U::UnitSystem) = energy(𝟐^5*𝟓^4*𝟑^2/𝟒𝟑,U,International)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²Ωᵢₜ⁻¹Vᵢₜ²2⁴3²5⁴43⁻¹ = 5.1138185304(16) × 10¹⁶) [𝘤²mₑ⋅g₀⁻¹] Unified
```

Heat energy required to raise 1 kg of water by 1 Kelvin (`kcal`) in `International` units.

```Julia
julia> kilocalorie(International) # J
2⁵3²5⁴43⁻¹ = 4186.0465116279065 [J] International

julia> kilocalorie(Metric) # J
Ωᵢₜ⁻¹Vᵢₜ²2⁵3²5⁴43⁻¹ = 4186.737323211056 [J] Metric

julia> kilocalorie(English) # ft⋅lb
g₀⁻¹ft⁻¹lb⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁵3²5⁴43⁻¹ = 3087.978978566891 [lbf⋅ft] English
```
