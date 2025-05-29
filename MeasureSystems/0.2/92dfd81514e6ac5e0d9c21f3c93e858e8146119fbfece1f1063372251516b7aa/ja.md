```Julia
meancalorie(U::UnitSystem) = energy(𝟐^2*𝟓*𝟑^2/𝟒𝟑,U,InternationalMean)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅1.0001900224889804 [𝘤²mₑ⋅g₀⁻¹] 統一

水1gを1ケルビン上昇させるのに必要な熱エネルギー（`cal`）を`InternationalMean`単位で。

```

Julia julia> meancalorie(InternationalMean) # J 2²3²5⋅43⁻¹ = 4.186046511627907 [J] InternationalMean

julia> meancalorie(Metric) # J 2²3²5⋅43⁻¹⋅1.0001900224889804 = 4.186841954605034 [J] Metric

julia> meancalorie(English) # ft⋅lb g₀⁻¹ft⁻¹lb⁻¹2²3²5⋅43⁻¹⋅1.0001900224889804 = 3.0880561507227156 [lbf⋅ft] English ```
