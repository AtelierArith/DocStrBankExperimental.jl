```Julia
statmho(U::UnitSystem) = conductance(𝟏,U,ESU)
conductance : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
F⁻¹L⁻¹T⁻¹Q²⋅(𝘤⁻¹τ⋅2⁻¹5⁻² = 4.1916900439033643×10⁻¹⁰) [𝘤⁻¹μ₀⁻¹λ⁻¹αL⁻²] Unified
```

Electrostatic unit of `conductance` (S).

```Julia
julia> statmho(Metric) # S
𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [S] Metric

julia> statmho(EMU) # abS
𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻¹s] EMU

julia> statmho(ESU) # statS
𝟏 = 1.0 [cm⋅s⁻¹] ESU
```
