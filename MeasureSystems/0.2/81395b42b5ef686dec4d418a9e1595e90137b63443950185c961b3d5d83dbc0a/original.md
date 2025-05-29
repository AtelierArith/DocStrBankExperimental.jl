```Julia
EMU = GaussSystem(Metric,𝟏,𝟐*τ)
F=MLT⁻², M=M, L=L, T=T, Q=M¹ᐟ²L¹ᐟ², Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Centimetre-gram-second `UnitSystem` variant based on `EMU` (non-rationalized).

```Julia
julia> boltzmann(EMU) # erg⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2¹¹5¹⁰ = 1.38064899953(43) × 10⁻¹⁶ [erg⋅K⁻¹] EMU

julia> planckreduced(EMU) # erg⋅s⋅rad⁻¹
𝘩⋅τ⁻¹2⁷5⁷ = 1.0545718176461565×10⁻²⁷ [erg⋅s] EMU

julia> lightspeed(EMU) # cm⋅s⁻¹
𝘤⋅2²5² = 2.99792458×10¹⁰ [cm⋅s⁻¹] EMU

julia> vacuumpermeability(EMU) # abH⋅cm⁻¹
𝟏 = 1.0 [𝟙] EMU

julia> electronmass(EMU) # g
𝘩⋅𝘤⁻¹R∞⋅α⁻²2⁴5³ = 9.1093837016(28) × 10⁻²⁸ [g] EMU

julia> molarmass(EMU) # g⋅mol⁻¹
𝟏 = 1.0 [g⋅mol⁻¹] EMU

julia> luminousefficacy(EMU) # lm⋅s⋅erg⁻¹
Kcd⋅2⁻⁷5⁻⁷ = 6.830196900900899×10⁻⁵ [lm⋅s⋅erg⁻¹] EMU

julia> rationalization(EMU)
τ⋅2 = 12.566370614359172 [𝟙] EMU
```
