```Julia
biotsavart(U::UnitSystem) = vacuumpermeability(U)*lorentz(U)*rationalization(U)/𝟐/τ
nonstandard : [FT²Q⁻²C], [FT²Q⁻²], [MLQ⁻²], [𝟙], [L⁻²T²]
FT²Q⁻²C⋅(τ⁻¹2⁻¹ = 0.07957747154594767) [μ₀⋅λ⋅αL] Unified
```

Magnetostatic proportionality constant `αB` for the Biot-Savart's law (H/m).

```Julia
julia> biotsavart(Metric) # H⋅m⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [H⋅m⁻¹] Metric

julia> biotsavart(CODATA) # H⋅m⁻¹
𝘤⁻¹α⋅RK⋅τ⁻¹ = 1.00000000040(28) × 10⁻⁷ [H⋅m⁻¹] CODATA

julia> biotsavart(SI2019) # H⋅m⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹ = 1.00000000055(15) × 10⁻⁷ [H⋅m⁻¹] SI2019

julia> biotsavart(Conventional) # H⋅m⁻¹
𝘤⁻¹α⋅RK90⋅τ⁻¹ = 9.9999998275(15) × 10⁻⁸ [H⋅m⁻¹] Conventional

julia> biotsavart(International) # H⋅m⁻¹
Ωᵢₜ⁻¹2⁻⁷5⁻⁷ = 9.995052449037726×10⁻⁸ [H⋅m⁻¹] International

julia> biotsavart(InternationalMean) # H⋅m⁻¹
2⁻⁷5⁻⁷/1.00049 = 9.995102399824085×10⁻⁸ [H⋅m⁻¹] InternationalMean

julia> biotsavart(EMU) # abH⋅cm⁻¹
𝟏 = 1.0 [𝟙] EMU

julia> biotsavart(ESU) # statH⋅cm⁻¹
𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻²s²] ESU

julia> biotsavart(Gauss) # abH⋅cm⁻¹
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] Gauss

julia> biotsavart(HLU) # hlH⋅cm⁻¹
𝘤⁻¹τ⁻¹2⁻³5⁻² = 2.654418729438073×10⁻¹² [cm⁻¹s] LorentzHeaviside
```
