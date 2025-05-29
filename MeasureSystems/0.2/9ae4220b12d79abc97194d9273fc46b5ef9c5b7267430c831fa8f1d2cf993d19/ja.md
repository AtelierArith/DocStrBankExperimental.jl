```Julia
joule(U::UnitSystem) = energy(𝟏,U,Metric)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²2⁻¹ = 1.22143285705(37) × 10¹³) [𝘤²mₑ⋅g₀⁻¹] 統一

Metric unit of `energy` (J or lb⋅ft).

```

Julia julia> joule(Metric) # J 𝟏 = 1.0 [J] Metric

julia> joule(CGS) # erg 2⁷5⁷ = 1.0×10⁷ [erg] Gauss

julia> joule(British) # lb⋅ft g₀⁻¹ft⁻¹lb⁻¹ = 0.7375621492772653 [lb⋅ft] British ```
