```Julia
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
resistance(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)/current(U,S)
resistance(v::Real,U::UnitSystem,S::UnitSystem) = v/resistance(U,S)
FLTQ⁻² [𝘤⋅μ₀⋅λ⋅αL²] Unified
```

Electrical `resistance` or `electricpotential` per `current` (Ω, S⁻¹, V⋅A⁻¹), unit conversion factor.

```Julia
julia> resistance(EMU,Metric) # Ω⋅abΩ⁻¹
2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> resistance(ESU,Metric) # Ω⋅statΩ⁻¹
𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> resistance(Metric,SI2019) # Ω⋅Ω⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
