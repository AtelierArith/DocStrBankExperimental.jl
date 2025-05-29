```Julia
conductance : [F⁻¹L⁻¹T⁻¹Q²], [F⁻¹L⁻¹T⁻¹Q²], [M⁻¹L⁻²TQ²], [L⁻¹T], [LT⁻¹]
conductance(U::UnitSystem,S::UnitSystem) = current(U,S)/electricpotential(U,S)
conductance(v::Real,U::UnitSystem,S::UnitSystem) = v/conductance(U,S)
F⁻¹L⁻¹T⁻¹Q² [𝘤⁻¹μ₀⁻¹λ⁻¹αL⁻²] Unified
```

Electrical `conductance` or `current` per `electricpotential` (S, Ω⁻¹, A⋅V⁻¹), unit conversion factor.

```Julia
julia> conductance(EMU,Metric) # S⋅abS⁻¹
2⁹5⁹ = 1.0×10⁹ [F]/[cm⁻¹s²] EMU -> Metric

julia> conductance(ESU,Metric) # S⋅statS⁻¹
𝘤⁻²2⁵5⁵ = 1.1126500560536183×10⁻¹² [F]/[cm] ESU -> Metric

julia> conductance(Metric,SI2019) # S⋅S⁻¹
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
