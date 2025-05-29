```Julia
Gauss = GaussSystem(Metric,𝟏,𝟐*τ,𝟏𝟎^-2/𝘤)
F=MLT⁻², M=M, L=L, T=T, Q=M¹ᐟ²L³ᐟ²T⁻¹, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=LT⁻¹
```

Centimetre-gram-second `UnitSystem` variant `CGS` (Gauss-Lorentz, non-rationalized).

```Julia
julia> boltzmann(Gauss) # erg⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2¹¹5¹⁰ = 1.38064899953(43) × 10⁻¹⁶ [erg⋅K⁻¹] Gauss

julia> planckreduced(Gauss) # erg⋅s⋅rad⁻¹
𝘩⋅τ⁻¹2⁷5⁷ = 1.0545718176461565×10⁻²⁷ [erg⋅s] Gauss

julia> lightspeed(Gauss) # cm⋅s⁻¹
𝘤⋅2²5² = 2.99792458×10¹⁰ [cm⋅s⁻¹] Gauss

julia> vacuumpermeability(Gauss) # statH⋅cm⁻¹
𝟏 = 1.0 [𝟙] Gauss

julia> electronmass(Gauss) # g
𝘩⋅𝘤⁻¹R∞⋅α⁻²2⁴5³ = 9.1093837016(28) × 10⁻²⁸ [g] Gauss

julia> molarmass(Gauss) # g⋅mol⁻¹
𝟏 = 1.0 [g⋅mol⁻¹] Gauss

julia> luminousefficacy(Gauss) # lm⋅s⋅erg⁻¹
Kcd⋅2⁻⁷5⁻⁷ = 6.830196900900899×10⁻⁵ [lm⋅s⋅erg⁻¹] Gauss

julia> rationalization(Gauss)
τ⋅2 = 12.566370614359172 [𝟙] Gauss

julia> lorentz(Gauss)
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] Gauss
```
