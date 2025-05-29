```Julia
magnetostatic(U::UnitSystem) = lorentz(U)*biotsavart(U) # electrostatic(U)/lightspeed(U)^2
nonstandard : [FT²Q⁻²], [FT²Q⁻²], [MLQ⁻²], [𝟙], [L⁻²T²]
FT²Q⁻²⋅(τ⁻¹2⁻¹ = 0.07957747154594767) [μ₀⋅λ⋅αL²] Unified
```

Magnetic proportionality constant `kₘ` for the Ampere's law force (N·s²⋅C⁻²).

```Julia
julia> magnetostatic(Metric) # H⋅m⁻¹
2⁻⁷5⁻⁷ = 1.0×10⁻⁷ [H⋅m⁻¹] Metric

julia> magnetostatic(CODATA) # H⋅m⁻¹
𝘤⁻¹α⋅RK⋅τ⁻¹ = 1.00000000040(28) × 10⁻⁷ [H⋅m⁻¹] CODATA

julia> magnetostatic(SI2019) # H⋅m⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹ = 1.00000000055(15) × 10⁻⁷ [H⋅m⁻¹] SI2019

julia> magnetostatic(Conventional) # H⋅m⁻¹
𝘤⁻¹α⋅RK90⋅τ⁻¹ = 9.9999998275(15) × 10⁻⁸ [H⋅m⁻¹] Conventional

julia> magnetostatic(International) # H⋅m⁻¹
Ωᵢₜ⁻¹2⁻⁷5⁻⁷ = 9.995052449037726×10⁻⁸ [H⋅m⁻¹] International

julia> magnetostatic(EMU) # abH⋅m⁻¹
𝟏 = 1.0 [𝟙] EMU

julia> magnetostatic(ESU) # statH⋅m⁻¹
𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻²s²] ESU

julia> magnetostatic(HLU) # hlH⋅m⁻¹
𝘤⁻²τ⁻¹2⁻⁵5⁻⁴ = 8.85418781762039×10⁻²³ [cm⁻²s²] LorentzHeaviside
```
