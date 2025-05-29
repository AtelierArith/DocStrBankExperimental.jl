```Julia
atmosphere(U::UnitSystem) = pressure(atm = 101325.0,U)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸atm⋅τ⁻³2⁻⁴ = 7.1266527568(87) × 10⁻²⁰) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

標準の `pressure` 参照レベルは1気圧 `atm` (Paまたはlb⋅ft⁻²) です。

```Julia
julia> atmosphere(Metric) # Pa
atm = 101325.0 [Pa] Metric

julia> atmosphere(English) # lb⋅ft⁻²
g₀⁻¹ft²lb⁻¹atm = 2116.2166236739367 [lbf⋅ft⁻²] English

julia> atmosphere(IPS) # lb⋅in⁻²
g₀⁻¹ft²lb⁻¹atm⋅2⁻⁴3⁻² = 14.695948775513449 [lb⋅in⁻²] IPS
```
