```Julia
inductance : [FLT²Q⁻²], [FLT²Q⁻²], [ML²Q⁻²], [L], [L⁻¹T²]
inductance(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/current(U,S)
inductance(v::Real,U::UnitSystem,S::UnitSystem) = v/inductance(U,S)
FLT²Q⁻² [ħ⋅𝘤⁻¹μ₀⋅mₑ⁻¹ϕ⋅λ⋅αL²g₀] Unified
```

Electro-`magneticflux` per `current` or `inductance` (H, Ω⋅s, Wb⋅A⁻¹), unit conversion factor.

```Julia
julia> inductance(EMU,Metric) # H⋅abH⁻¹
2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [F⁻¹]/[gal] EMU -> Metric

julia> inductance(ESU,Metric) # H⋅statH⁻¹
𝘤²2⁻⁵5⁻⁵ = 8.987551787368176×10¹¹ [F⁻¹]/[cm⁻¹] ESU -> Metric

julia> inductance(Metric,SI2019) # H⋅H⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
