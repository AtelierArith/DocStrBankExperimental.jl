```Julia
capacitance : [F⁻¹L⁻¹Q²], [F⁻¹L⁻¹Q²], [M⁻¹L⁻²T²Q²], [L⁻¹T²], [L]
capacitance(U::UnitSystem,S::UnitSystem) = charge(U,S)/electricpotential(U,S)
capacitance(v::Real,U::UnitSystem,S::UnitSystem) = v/capacitance(U,S)
F⁻¹L⁻¹Q² [ħ⋅𝘤⁻³μ₀⁻¹mₑ⁻¹ϕ⋅λ⁻¹αL⁻²g₀] Unified
```

Electrical `capactiance` or `charge` per `electricpotential` (F, C⋅V⁻¹), unit conversion factor.

```Julia
julia> capacitance(EMU,Metric) # F⋅abF⁻¹
2⁹5⁹ = 1.0×10⁹ [F]/[cm⁻¹s²] EMU -> Metric

julia> capacitance(ESU,Metric) # F⋅cm⁻¹
𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [F]/[cm] ESU -> Metric

julia> capactiance(Metric,SI2019) # F⋅F⁻¹
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
