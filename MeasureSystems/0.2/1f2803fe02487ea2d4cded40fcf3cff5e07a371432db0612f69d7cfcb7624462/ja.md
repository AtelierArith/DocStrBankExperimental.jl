```Julia
ESU = GaussSystem(Metric,(𝟏𝟎*𝘤)^-2,𝟐*τ)
F=MLT⁻², M=M, L=L, T=T, Q=M¹ᐟ²L³ᐟ²T⁻¹, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

センチメートル-グラム-秒 `UnitSystem` のバリアント、`ESU`（非合理化）。

```Julia
julia> boltzmann(ESU) # erg⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2¹¹5¹⁰ = 1.38064899953(43) × 10⁻¹⁶ [erg⋅K⁻¹] ESU

julia> planckreduced(ESU) # erg⋅s⋅rad⁻¹
𝘩⋅τ⁻¹2⁷5⁷ = 1.0545718176461565×10⁻²⁷ [erg⋅s] ESU

julia> lightspeed(ESU) # cm⋅s⁻¹
𝘤⋅2²5² = 2.99792458×10¹⁰ [cm⋅s⁻¹] ESU

julia> vacuumpermeability(ESU) # statH⋅cm⁻¹
𝘤⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻²s²] ESU

julia> electronmass(ESU) # g
𝘩⋅𝘤⁻¹R∞⋅α⁻²2⁴5³ = 9.1093837016(28) × 10⁻²⁸ [g] ESU

julia> molarmass(ESU) # g⋅mol⁻¹
𝟏 = 1.0 [g⋅mol⁻¹] ESU

julia> luminousefficacy(ESU) # lm⋅s⋅erg⁻¹
Kcd⋅2⁻⁷5⁻⁷ = 6.830196900900899×10⁻⁵ [lm⋅s⋅erg⁻¹] ESU

julia> rationalization(ESU)
τ⋅2 = 12.566370614359172 [𝟙] ESU
```
