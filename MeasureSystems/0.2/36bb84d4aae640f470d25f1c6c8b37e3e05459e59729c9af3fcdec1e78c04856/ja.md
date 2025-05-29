```Julia
earthmass(U::UnitSystem) = mass(𝘩⁻¹𝘤⁻¹mP²GME⋅τ = 5.97217(13) × 10²⁴,U)
mass : [M], [FL⁻¹T²], [M], [M], [M]
M⋅(𝘩⁻²R∞⁻¹α²mP²GME⋅τ⋅2⁻¹ = 6.55606(14) × 10⁵⁴) [mₑ] Unified
```

地球の `mass` は重力定数の推定値から算出されます (kg または slug)。

```Julia
julia> earthmass(Metric) # kg
𝘩⁻¹𝘤⁻¹mP²GME⋅τ = 5.97217(13) × 10²⁴ [kg] Metric

julia> earthmass(British) # slug
𝘩⁻¹𝘤⁻¹g₀⁻¹ft⋅lb⁻¹mP²GME⋅τ = 4.092234(90) × 10²³ [slug] British

julia> earthmass(English) # lb
𝘩⁻¹𝘤⁻¹lb⁻¹mP²GME⋅τ = 1.316637(29) × 10²⁵ [lbm] English

julia> earthmass(IAU) # M☉
au⁻³kG⁻²GME⋅τ⁻²2²⁸3¹⁴5¹⁰ = 3.0034896577(60) × 10⁻⁶ [M☉] IAU☉

julia> earthmass(IAUJ) # MJ
GME⋅GMJ⁻¹ = 0.00314635210(22) [MJ] IAUJ

julia> earthmass(QCD) # mₚ
𝘩⁻²R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹mP²GME⋅τ⋅2⁻¹ = 3.570542(79) × 10⁵¹ [mₚ] QCD

julia> earthmass(Metric)/dalton(Metric) # Da
𝘩⁻²R∞⁻¹α²μₑᵤ⋅mP²GME⋅τ⋅2⁻¹ = 3.596523(79) × 10⁵¹ [𝟙] Metric
```
