```Julia
flick(U::UnitSystem) = radiance(𝟏𝟎^10,U,Metric)/length(𝟏,U,Metric)
nonstandard : [FL⁻²T⁻¹A⁻²], [FL⁻²T⁻¹], [ML⁻¹T⁻³], [ML⁻¹T⁻³], [ML⁻¹T⁻³]
FL⁻²T⁻¹A⁻²⋅(𝘩⁻¹𝘤⁻²R∞⁻⁵α¹⁰τ⁻⁴2⁵5¹⁰ = 9.059719376(14) × 10⁻³⁶) [ħ⁻⁴𝘤⁷mₑ⁵ϕ⁻⁶g₀⁻⁵] Unified
```

ロッキード・マーチンの `radiance` の単位は `length` あたり (W⋅m⁻³⋅rad⁻²) です。

```Julia
julia> flick(Metric) # W⋅m⁻³
2¹⁰5¹⁰ = 1.0×10¹⁰ [W⋅m⁻³] Metric

julia> flick(CGS) # erg⋅s⁻¹⋅mL⁻¹
2¹¹5¹¹ = 1.0×10¹¹ [erg⋅s⁻¹mL⁻¹] Gauss

julia> flick(MetricSpatian) # W⋅m⁻³⋅ς⁻²
τ⋅2¹¹5¹⁰ = 1.2566370614359172×10¹¹ [W⋅m⁻³⋅ς⁻²] MetricSpatian
```
