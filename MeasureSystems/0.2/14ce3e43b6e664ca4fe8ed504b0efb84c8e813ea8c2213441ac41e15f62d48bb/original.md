```Julia
calorie(U::UnitSystem) = kilocalorie(U)/𝟐^3/𝟓^3
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²Ωᵢₜ⁻¹Vᵢₜ²2⋅3²5⋅43⁻¹ = 5.1138185304(16) × 10¹³) [𝘤²mₑ⋅g₀⁻¹] Unified
```

Heat energy required to raise 1 g of water by 1 Kelvin (`cal`) in `International` units.

```Julia
julia> calorie(International) # J
2²3²5⋅43⁻¹ = 4.186046511627907 [J] International

julia> calorie(Metric) # J
Ωᵢₜ⁻¹Vᵢₜ²2²3²5⋅43⁻¹ = 4.186737323211057 [J] Metric

julia> calorie(English) # ft⋅lb
g₀⁻¹ft⁻¹lb⁻¹Ωᵢₜ⁻¹Vᵢₜ²2²3²5⋅43⁻¹ = 3.087978978566891 [lbf⋅ft] English
```
