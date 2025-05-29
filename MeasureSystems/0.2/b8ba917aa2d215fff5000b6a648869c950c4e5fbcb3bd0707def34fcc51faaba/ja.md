```Julia
torr(U::UnitSystem) = pressure(atm/𝟐^3/𝟓/𝟏𝟗,U,Metric)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸atm⋅τ⁻³2⁻⁷5⁻¹19⁻¹ = 9.377174680(11) × 10⁻²³) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

1 mmの水銀によって標準大気条件下で加えられる`pressure`の単位。

```Julia
juila> torr(Metric) # Pa
atm⋅2⁻³5⁻¹19⁻¹ = 133.32236842105263 [Pa] Metric

julia> torr(English) # lb⋅ft⁻²
g₀⁻¹ft²lb⁻¹atm⋅2⁻³5⁻¹19⁻¹ = 2.784495557465706 [lbf⋅ft⁻²] English

julia> torr(IPS) # lb⋅in⁻²
g₀⁻¹ft²lb⁻¹atm⋅2⁻⁷3⁻²5⁻¹19⁻¹ = 0.01933677470462296 [lb⋅in⁻²] IPS
```
