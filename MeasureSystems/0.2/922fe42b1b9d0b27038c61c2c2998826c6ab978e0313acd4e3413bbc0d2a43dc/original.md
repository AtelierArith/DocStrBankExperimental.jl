```Julia
ohm(U::UnitSystem) = resistance(𝟏,U,Metric)
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
FLTQ⁻²⋅(𝘤⁻¹τ⁻¹2⁶5⁷ = 0.0026544187294380724) [𝘤⋅μ₀⋅λ⋅αL²] Unified
```

Metric unit of `resistance` (Ω).

```Julia
julia> ohm(Metric) # Ω
𝟏 = 1.0 [Ω] Metric

julia> ohm(EMU) # abΩ
2⁹5⁹ = 1.0×10⁹ [cm⋅s⁻¹] EMU

julia> ohm(ESU) # statΩ
𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [cm⁻¹s] ESU
```
