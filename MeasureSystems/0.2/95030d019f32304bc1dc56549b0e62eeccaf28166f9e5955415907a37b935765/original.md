```Julia
resistivity : [FL²TQ⁻²], [FL²TQ⁻²], [ML³T⁻¹Q⁻²], [L²T⁻¹], [T]
resistivity(U::UnitSystem,S::UnitSystem) = resistance(U,S)*length(U,S)
resistivity(v::Real,U::UnitSystem,S::UnitSystem) = v/resistivity(U,S)
FL²TQ⁻² [ħ⋅μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] Unified
```

Electrical `resistivity` or `resistance` by `length` (Ω⋅m), unit conversion factor.

```Julia
julia> resistance(EMU,Metric) # Ω⋅m⋅abΩ⁻¹⋅cm⁻¹
2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> resistance(ESU,Metric) # Ω⋅m⋅statΩ⁻¹⋅cm⁻¹
𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> resistance(Metric,SI2019) # Ω⋅Ω⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
