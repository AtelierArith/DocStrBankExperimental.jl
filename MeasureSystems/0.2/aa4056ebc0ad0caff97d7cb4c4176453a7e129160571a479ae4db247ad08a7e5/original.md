```Julia
permittivity : [F⁻¹L⁻²Q²R], [F⁻¹L⁻²Q²], [M⁻¹L⁻³T²Q²], [L⁻²T²], [𝟙]
permittivity(U::UnitSystem,S::UnitSystem) = capacitance(U,S)*rationalization(U,S)/length(U,S)
permittivity(v::Real,U::UnitSystem,S::UnitSystem) = v/permittivity(U,S)
F⁻¹L⁻²Q²R [𝘤⁻²μ₀⁻¹αL⁻²] Unified
```

Absolute `permittivity` or `capacitance` per `length` (F⋅m⁻¹), unit conversion factor.

```Julia
julia> permittivity(EMU,Metric) # F⋅cm⋅abF⁻¹⋅m⁻¹
τ⁻¹2¹⁰5¹¹ = 7.957747154594768×10⁹ [F⋅m⁻¹]/[cm⁻²s²] EMU -> Metric

julia> permittivity(ESU,Metric) # F⋅m⁼¹
𝘤⁻²τ⁻¹2⁶5⁷ = 8.854187817620389×10⁻¹² [F⋅m⁻¹]/[𝟙] ESU -> Metric

julia> permittivity(Metric,SI2019) # F⋅F⁻¹
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
