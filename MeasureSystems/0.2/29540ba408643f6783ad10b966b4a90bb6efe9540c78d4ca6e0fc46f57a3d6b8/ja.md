```Julia
lumerg(U::UnitSystem) = luminousenergy(𝟏𝟎^-7,U,Metric)
luminousenergy : [TJ], [TJ], [TJ], [TJ], [TJ]
TJ⋅(𝘩⁻¹𝘤⁻¹Kcd⁻¹R∞⁻¹α²2⁻⁸5⁻⁷ = 1788.28352208(55)) [𝘤²mₑ⋅Kcd⋅g₀⁻¹] Unified
```

`luminousenergy` の基準単位 (lm⋅s)。

```Julia
julia> lumerg(CGS) # lm⋅s
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [s⋅lm] Gauss
```
