```Julia
pascal(U::UnitSystem) = pressure(𝟏,U,Metric)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸τ⁻³2⁻⁴ = 7.0334594194(86) × 10⁻²⁵) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Metric unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> pascal(Metric) # Pa
𝟏 = 1.0 [Pa] Metric

julia> pascal(English) # lb⋅ft⁻²
g₀⁻¹ft²lb⁻¹ = 0.02088543423315013 [lbf⋅ft⁻²] English

julia> pascal(IPS) # lb⋅in⁻²
g₀⁻¹ft²lb⁻¹2⁻⁴3⁻² = 0.0001450377377302092 [lb⋅in⁻²] IPS
```
