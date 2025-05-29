```Julia
permeability : [FT²Q⁻²R⁻¹C²], [FT²Q⁻²], [MLQ⁻²], [𝟙], [L⁻²T²]
permeability(U::UnitSystem,S::UnitSystem) = permeability(S)/permeability(U)
permeability(v::Real,U::UnitSystem,S::UnitSystem) = v/permeability(U,S)
FT²Q⁻²R⁻¹C² [μ₀] Unified
```

Magnetic `permeability` or `inductance` per `length` (H⋅m⁻¹), unit conversion factor.

```Julia
julia> permeability(EMU,Metric) # H⋅cm⋅abH⁻¹⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [kg⋅m⋅s⁻²C⁻²]/[gal⋅cm⁻¹] EMU -> Metric

julia> permeability(ESU,Metric) # H⋅cm⋅statH⁻¹⋅m⁼¹
𝘤²τ⋅2⁻²5⁻³ = 1.129409066758147×10¹⁵ [kg⋅m⋅s⁻²C⁻²]/[cm⁻²] ESU -> Metric

julia> permeability(Metric,SI2019) # H⋅H⁻¹
𝘩⋅𝘤⁻¹𝘦⁻²α⋅τ⁻¹2⁷5⁷ = 1.00000000055(15) [C⁻²]/[C⁻²] Metric -> SI2019
```
