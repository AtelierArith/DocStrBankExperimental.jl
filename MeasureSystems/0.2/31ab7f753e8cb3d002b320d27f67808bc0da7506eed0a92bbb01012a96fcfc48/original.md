```Julia
conductivity : [F⁻¹L⁻²T⁻¹Q²], [F⁻¹L⁻²T⁻¹Q²], [M⁻¹L⁻³TQ²], [L⁻²T], [T⁻¹]
conductivity(U::UnitSystem,S::UnitSystem) = conductance(U,S)/length(U,S)
conductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/conductivity(U,S)
F⁻¹L⁻²T⁻¹Q² [ħ⁻¹μ₀⁻¹mₑ⋅ϕ⁻¹λ⁻¹αL⁻²g₀⁻¹] Unified
```

Reciprocal `resistivity` or electrical `conductivity` (S⋅m⁻¹), unit conversion factor.

```Julia
julia> conductivity(EMU,Metric) # S⋅cm⋅abS⁻¹⋅m⁻¹
2¹¹5¹¹ = 1.0×10¹¹ [F⋅m⁻¹]/[cm⁻²s²] EMU -> Metric

julia> conductivity(ESU,Metric) # S⋅cm⋅statS⁻¹⋅m⁼¹
𝘤⁻²2⁷5⁷ = 1.1126500560536183×10⁻¹⁰ [F⋅m⁻¹]/[𝟙] ESU -> Metric

julia> conductivity(Metric,SI2019) # S⋅S⁻¹
𝘩⁻¹𝘤⋅𝘦²α⁻¹τ⋅2⁻⁷5⁻⁷ = 0.99999999945(15) [C²]/[C²] Metric -> SI2019
```
