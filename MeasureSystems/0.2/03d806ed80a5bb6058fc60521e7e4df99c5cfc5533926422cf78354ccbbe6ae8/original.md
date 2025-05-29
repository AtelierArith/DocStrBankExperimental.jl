```Julia
MTS = EntropySystem(SI2019,𝟏,𝟏,kilo)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Metre-tonne-second `UnitSystem` variant of `Metric` system.

```Julia
julia> boltzmann(MTS) # kJ⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2 = 1.38064899953(43) × 10⁻²⁶ [t⋅m²s⁻²K⁻¹] MTS

julia> planckreduced(MTS) # kJ⋅s⋅rad⁻¹
𝘩⋅τ⁻¹2⁻³5⁻³ = 1.0545718176461566×10⁻³⁷ [t⋅m²s⁻¹] MTS

julia> lightspeed(MTS) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MTS

julia> vacuumpermeability(MTS) # kH⋅m⁻¹
τ⋅2⁻⁹5⁻¹⁰ = 1.2566370614359174×10⁻⁹ [t⋅m⋅C⁻²] MTS

julia> electronmass(MTS) # t
𝘩⋅𝘤⁻¹R∞⋅α⁻²2⁻²5⁻³ = 9.1093837016(28) × 10⁻³⁴ [t] MTS

julia> molarmass(MTS) # t⋅mol⁻¹
2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [t⋅mol⁻¹] MTS

julia> luminousefficacy(MTS) # lm⋅kW⁻¹
Kcd⋅2³5³ = 683019.6900900899 [t⁻¹m⁻²s³lm] MTS
```
