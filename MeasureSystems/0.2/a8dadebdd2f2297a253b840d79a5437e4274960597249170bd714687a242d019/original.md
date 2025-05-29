```Julia
statohm(U::UnitSystem) = resistance(𝟏,U,ESU)
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
FLTQ⁻²⋅(𝘤⋅τ⁻¹2⋅5² = 2.385672579618471×10⁹) [𝘤⋅μ₀⋅λ⋅αL²] Unified
```

Electrostatic unit of `resistance` (Ω).

```Julia
julia> statohm(Metric) # Ω
𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [Ω] Metric

julia> statohm(EMU) # abΩ
𝘤²2⁴5⁴ = 8.987551787368175×10²⁰ [cm⋅s⁻¹] EMU

julia> statohm(ESU) # statΩ
𝟏 = 1.0 [cm⁻¹s] ESU
```
