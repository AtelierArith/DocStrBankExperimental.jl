```Julia
lunarmass(U::UnitSystem) = earthmass(U)/μE☾
mass : [M], [FL⁻¹T²], [M], [M], [M]
M/81.300568 ± 3.0e-6 [mₑ] Unified
```

Lunar `mass` estimated from `μE☾` Earth-Moon mass ratio (kg or slug).

```Julia
julia> lunarmass(Metric) # kg
𝘩⁻¹𝘤⁻¹mP²GME⋅τ/81.3005680(30) = 7.34579(16) × 10²² [kg] Metric

julia> lunarmass(British) # slug
𝘩⁻¹𝘤⁻¹g₀⁻¹ft⋅lb⁻¹mP²GME⋅τ/81.3005680(30) = 5.03346(11) × 10²¹ [slug] British

julia> lunarmass(English) # lb
𝘩⁻¹𝘤⁻¹lb⁻¹mP²GME⋅τ/81.3005680(30) = 1.619469(36) × 10²³ [lbm] English

julia> lunarmass(IAU) # M☉
au⁻³kG⁻²GME⋅τ⁻²2²⁸3¹⁴5¹⁰/81.3005680(30) = 3.69430341(14) × 10⁻⁸ [M☉] IAU☉

julia> lunarmass(IAUE) # ME
𝟏/81.3005680(30) = 0.01230003707(45) [ME] IAUE

julia> lunarmass(IAUJ) # MJ
GME⋅GMJ⁻¹/81.3005680(30) = 3.87002474(31) × 10⁻⁵ [MJ] IAUJ

julia> lunarmass(QCD) # mₚ
𝘩⁻²R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹mP²GME⋅τ⋅2⁻¹/81.3005680(30) = 4.391780(97) × 10⁴⁹ [mₚ] QCD

julia> lunarmass(Metric)/dalton(Metric) # Da
𝘩⁻²R∞⁻¹α²μₑᵤ⋅mP²GME⋅τ⋅2⁻¹/81.3005680(30) = 4.423736(98) × 10⁴⁹ [𝟙] Metric
```
