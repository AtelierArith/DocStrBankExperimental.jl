```Julia
talbot(U::UnitSystem) = luminousenergy(𝟏,U,Metric)
luminousenergy : [TJ], [TJ], [TJ], [TJ], [TJ]
TJ⋅(𝘩⁻¹𝘤⁻¹Kcd⁻¹R∞⁻¹α²2⁻¹ = 1.78828352208(55) × 10¹⁰) [𝘤²mₑ⋅Kcd⋅g₀⁻¹] Unified
```

`luminousenergy` の共通単位 (lm⋅s)。

```Julia
julia> talbot(Metric) # lm⋅s
𝟏 = 1.0 [s⋅lm] Metric
```
