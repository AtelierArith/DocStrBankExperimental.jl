```Julia
thermalunit(U::UnitSystem) = kilocalorie(U)*𝟑^2/𝟓/lb
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁴5⁵43⁻¹ = 1.28866059275(39) × 10¹⁶) [𝘤²mₑ⋅g₀⁻¹] Unified
```

1 lbの水を1ランキン上昇させるために必要な熱エネルギー（`BTU`）を`International`単位で。

```Julia
julia> thermalunit(British) # ft⋅lb
g₀⁻¹ft⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁵5⁵43⁻¹ = 778.1576129990752 [lb⋅ft] British

julia> thermalunit(International) # J
lb⋅2⁵5⁵43⁻¹ = 1054.8659767441861 [J] International

julia> thermalunit(Metric) # J
lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁵5⁵43⁻¹ = 1055.0400583348662 [J] Metric
```
