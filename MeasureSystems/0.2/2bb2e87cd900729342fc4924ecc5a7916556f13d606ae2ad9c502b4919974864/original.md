```Julia
erg(U::UnitSystem) = energy(𝟏,U,Gauss)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²2⁻⁸5⁻⁷ = 1.22143285705(37) × 10⁶) [𝘤²mₑ⋅g₀⁻¹] Unified
```

Historical unit of `energy` (J or lb⋅ft).

```Julia
julia> erg(Metric) # J
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [J] Metric

julia> erg(CGS) # erg
𝟏 = 1.0 [erg] Gauss

julia> erg(British) # lb⋅ft
g₀⁻¹ft⁻¹lb⁻¹2⁻⁷5⁻⁷ = 7.375621492772652×10⁻⁸ [lb⋅ft] British
```
