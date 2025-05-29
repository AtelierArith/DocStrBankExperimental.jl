```Julia
psi(U::UnitSystem) = pressure(𝟏,U,IPS)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸g₀⋅ft⁻²lb⋅τ⁻³3² = 4.8493995628(59) × 10⁻²¹) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

English unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> psi(Metric) # Pa
g₀⋅ft⁻²lb⋅2⁴3² = 6894.75729316836 [Pa] Metric

julia> psi(English) # lb⋅ft⁻²
2⁴3² = 144.0 [lbf⋅ft⁻²] English

julia> psi(IPS) # lb⋅in⁻²
𝟏 = 1.0 [lb⋅in⁻²] IPS
```
