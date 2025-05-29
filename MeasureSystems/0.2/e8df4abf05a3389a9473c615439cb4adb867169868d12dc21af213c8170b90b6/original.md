```Julia
bar(U::UnitSystem) = pressure(hecto*kilo,U,Metric)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸τ⁻³2⋅5⁵ = 7.0334594194(86) × 10⁻²⁰) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Reference unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> bar(Metric) # Pa
2⁵5⁵ = 100000.0 [Pa] Metric

julia> bar(English) # lb⋅ft⁻²
g₀⁻¹ft²lb⁻¹2⁵5⁵ = 2088.543423315013 [lbf⋅ft⁻²] English

julia> bar(IPS) # lb⋅in⁻²
g₀⁻¹ft²lb⁻¹2⋅3⁻²5⁵ = 14.503773773020923 [lb⋅in⁻²] IPS
```
