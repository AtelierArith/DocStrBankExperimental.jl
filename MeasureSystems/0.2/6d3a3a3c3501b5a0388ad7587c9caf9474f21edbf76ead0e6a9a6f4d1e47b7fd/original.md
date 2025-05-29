```Julia
gasgallon(U::UnitSystem) = 𝟐*𝟑*𝟏𝟗*kilo*thermalunit(U)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
FL⋅(𝘩⁻¹𝘤⁻¹R∞⁻¹α²lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁸3⋅5⁸19⋅43⁻¹ = 1.46907307574(45) × 10²¹) [𝘤²mₑ⋅g₀⁻¹] Unified
```

Gasoline gallon equivalent reference unit of `energy` (J or lb⋅ft).

```Julia
julia> gasgallon(Metric) # J
lb⋅Ωᵢₜ⁻¹Vᵢₜ²2⁹3⋅5⁸19⋅43⁻¹ = 1.2027456665017475×10⁸ [J] Metric

julia> gasgallon(CGS) # erg
lb⋅Ωᵢₜ⁻¹Vᵢₜ²2¹⁶3⋅5¹⁵19⋅43⁻¹ = 1.2027456665017475×10¹⁵ [erg] Gauss

julia> gasgallon(British) # lb⋅ft
g₀⁻¹ft⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁹3⋅5⁸19⋅43⁻¹ = 8.870996788189459×10⁷ [lb⋅ft] British
```
