```Julia
abmho(U::UnitSystem) = conductance(𝟏,U,EMU)
conductance : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
F⁻¹L⁻¹T⁻¹Q²⋅(𝘤⋅τ⋅2³5² = 3.767303134617706×10¹¹) [𝘤⁻¹μ₀⁻¹λ⁻¹αL⁻²] Unified
```

Electromagnetic unit of `conductance` (S).

```Julia
julia> abmho(Metric) # S
2⁹5⁹ = 1.0×10⁹ [S] Metric

julia> abmho(EMU) # abS
𝟏 = 1.0 [cm⁻¹s] EMU

julia> abmho(ESU) # statS
𝘤²2⁴5⁴ = 8.987551787368175×10²⁰ [cm⋅s⁻¹] ESU
```
