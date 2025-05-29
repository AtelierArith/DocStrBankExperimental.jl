```Julia
footpound(U::UnitSystem) = poundforce(U)*foot(U)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²g₀⋅ft⋅lb⋅2⁻¹ = 1.65604059027(51) × 10¹³) [𝘤²mₑ⋅g₀⁻¹] Unified
```

重力および工学システムにおける`energy`の英単位（Jまたはlb⋅ft）。

```Julia
julia> footpound(Metric) # J
g₀⋅ft⋅lb = 1.3558179483314003 [J] Metric

julia> footpound(CGS) # erg
g₀⋅ft⋅lb⋅2⁷5⁷ = 1.3558179483314004×10⁷ [erg] Gauss

julia> footpound(British) # lb⋅ft
𝟏 = 1.0 [lb⋅ft] British
```
