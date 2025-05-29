```Julia
LorentzHeaviside = GaussSystem(Metric,𝟏,𝟏,centi/𝘤)
F=MLT⁻², M=M, L=L, T=T, Q=M¹ᐟ²L³ᐟ²T⁻¹, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=LT⁻¹
```

Centimetre-gram-second `UnitSystem` variant `HLU` (Heaviside-Lorentz, rationalized).

```Julia
julia> boltzmann(LorentzHeaviside) # erg⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2¹¹5¹⁰ = 1.38064899953(43) × 10⁻¹⁶ [erg⋅K⁻¹] LorentzHeaviside

julia> planckreduced(LorentzHeaviside) # erg⋅s⋅rad⁻¹
𝘩⋅τ⁻¹2⁷5⁷ = 1.0545718176461565×10⁻²⁷ [erg⋅s] LorentzHeaviside

julia> lightspeed(LorentzHeaviside) # cm⋅s⁻¹
𝘤⋅2²5² = 2.99792458×10¹⁰ [cm⋅s⁻¹] LorentzHeaviside

julia> vacuumpermeability(HLU) # hlH⋅cm⁻¹
𝟏 = 1.0 [𝟙] LorentzHeaviside

julia> electronmass(LorentzHeaviside) # g
𝘩⋅𝘤⁻¹R∞⋅α⁻²2⁴5³ = 9.1093837016(28) × 10⁻²⁸ [g] LorentzHeaviside

julia> molarmass(LorentzHeaviside) # g⋅mol⁻¹
𝟏 = 1.0 [g⋅mol⁻¹] LorentzHeaviside

julia> luminousefficacy(LorentzHeaviside) # lm⋅s⋅erg⁻¹
Kcd⋅2⁻⁷5⁻⁷ = 6.830196900900899×10⁻⁵ [lm⋅s⋅erg⁻¹] LorentzHeaviside

julia> rationalization(LorentzHeaviside)
𝟏 = 1.0 [𝟙] LorentzHeaviside

julia> lorentz(LorentzHeaviside)
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [cm⁻¹s] LorentzHeaviside
```
