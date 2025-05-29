```Julia
Gravitational = EntropySystem(Metric,𝟏,𝟏,g₀)
F=F, M=FL⁻¹T², L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Standard `Gravitational` system based on `hyl` and `kilopond` units.

```Julia
julia> boltzmann(Gravitational) # kgf⋅m⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹2⁴5³ = 1.40787016925(43) × 10⁻²⁴ [kgf⋅m⋅K⁻¹] Gravitational

julia> planckreduced(Gravitational) # kgf⋅m⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹τ⁻¹ = 1.0753639802033891×10⁻³⁵ [kgf⋅m⋅s] Gravitational

julia> lightspeed(Gravitational) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] Gravitational

julia> vacuumpermeability(Gravitational) # H⋅m⁻¹
g₀⁻¹τ⋅2⁻⁶5⁻⁷ = 1.2814131853751459×10⁻⁷ [kgf⋅s²C⁻²] Gravitational

julia> electronmass(Gravitational) # hyl
𝘩⋅𝘤⁻¹R∞⋅α⁻²g₀⁻¹2 = 9.2889862507(28) × 10⁻³² [hyl] Gravitational

julia> molarmass(Gravitational) # hyl⋅mol⁻¹
g₀⁻¹2⁻³5⁻³ = 0.00010197162129779284 [hyl⋅mol⁻¹] Gravitational

julia> luminousefficacy(Gravitational) # lm⋅s⋅m⁻¹⋅kgf⁻¹
Kcd⋅g₀ = 6698.135043821981 [kgf⁻¹m⁻¹s⋅lm] Gravitational
```
