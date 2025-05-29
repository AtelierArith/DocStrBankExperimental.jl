```Julia
meancalorie(U::UnitSystem) = energy(𝟐^2*𝟓*𝟑^2/𝟒𝟑,U,InternationalMean)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅1.0001900224889804 [𝘤²mₑ⋅g₀⁻¹] Unified
```

Heat energy required to raise 1 g of water by 1 Kelvin (`cal`) in `InternationalMean` units.

```Julia
julia> meancalorie(InternationalMean) # J
2²3²5⋅43⁻¹ = 4.186046511627907 [J] InternationalMean

julia> meancalorie(Metric) # J
2²3²5⋅43⁻¹⋅1.0001900224889804 = 4.186841954605034 [J] Metric

julia> meancalorie(English) # ft⋅lb
g₀⁻¹ft⁻¹lb⁻¹2²3²5⋅43⁻¹⋅1.0001900224889804 = 3.0880561507227156 [lbf⋅ft] English
```
