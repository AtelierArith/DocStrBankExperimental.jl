```Julia
tontnt(U::UnitSystem) = giga*calorie(U)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²Ωᵢₜ⁻¹Vᵢₜ²2¹⁰3²5¹⁰43⁻¹ = 5.1138185304(16) × 10²²) [𝘤²mₑ⋅g₀⁻¹] Unified
```

トン TNT 相当の基準単位 `energy` (J または lb⋅ft)。

```Julia
julia> tontnt(Metric) # J
Ωᵢₜ⁻¹Vᵢₜ²2¹¹3²5¹⁰43⁻¹ = 4.186737323211056×10⁹ [J] Metric

julia> tontnt(CGS) # erg
Ωᵢₜ⁻¹Vᵢₜ²2¹⁸3²5¹⁷43⁻¹ = 4.186737323211057×10¹⁶ [erg] Gauss

julia> tontnt(British) # lb⋅ft
g₀⁻¹ft⁻¹lb⁻¹Ωᵢₜ⁻¹Vᵢₜ²2¹¹3²5¹⁰43⁻¹ = 3.087978978566891×10⁹ [lb⋅ft] British
```
