```Julia
electrostatic(U::UnitSystem) = rationalization(U)/𝟐/τ/vacuumpermittivity(U)
nonstandard : [FL²Q⁻²], [FL²Q⁻²], [ML³T⁻²Q⁻²], [L²T⁻²], [𝟙]
FL²Q⁻²⋅(τ⁻¹2⁻¹ = 0.07957747154594767) [𝘤²μ₀⋅λ⋅αL²] Unified
```

Electrostatic proportionality constant `kₑ` for the Coulomb's law force (N⋅m²⋅C⁻²).

```Julia
julia> electrostatic(Metric) # N⋅m²⋅C⁻²
𝘤²2⁻⁷5⁻⁷ = 8.987551787368176×10⁹ [m⋅F⁻¹] Metric

julia> electrostatic(CODATA) # N·m²⋅C⁻²
𝘤⋅α⋅RK⋅τ⁻¹ = 8.9875517909(25) × 10⁹ [m⋅F⁻¹] CODATA

julia> electrostatic(SI2019) # N·m²⋅C⁻²
𝘩⋅𝘤⋅𝘦⁻²α⋅τ⁻¹ = 8.9875517923(14) × 10⁹ [m⋅F⁻¹] SI2019

julia> electrostatic(Conventional) # N·m²⋅C⁻²
𝘤⋅α⋅RK90⋅τ⁻¹ = 8.9875516323(14) × 10⁹ [m⋅F⁻¹] Conventional

julia> electrostatic(International) # N·m²⋅C⁻²
𝘤²Ωᵢₜ⁻¹2⁻⁷5⁻⁷ = 8.983105150318768×10⁹ [m⋅F⁻¹] International

julia> electrostatic(EMU) # dyn⋅cm²⋅abC⁻²
𝘤²2⁴5⁴ = 8.987551787368175×10²⁰ [erg⋅g⁻¹] EMU

julia> electrostatic(ESU) # dyn⋅cm²⋅statC⁻²
𝟏 = 1.0 [𝟙] ESU

julia> electrostatic(HLU) # dyn⋅cm²⋅hlC⁻²
τ⁻¹2⁻¹ = 0.07957747154594767 [𝟙] LorentzHeaviside
```
