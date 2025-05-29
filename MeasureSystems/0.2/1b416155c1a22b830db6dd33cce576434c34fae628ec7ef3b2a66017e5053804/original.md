```Julia
Metric = MetricSystem(milli,𝟐*τ/𝟏𝟎^7)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Standard `Metric` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(Metric) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] Metric

julia> planckreduced(Metric) # J⋅s⋅rad⁻¹
𝘩⋅τ⁻¹ = 1.0545718176461565×10⁻³⁴ [J⋅s] Metric

julia> lightspeed(Metric) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] Metric

julia> vacuumpermeability(Metric) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] Metric

julia> electronmass(Metric) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] Metric

julia> molarmass(Metric) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] Metric

julia> luminousefficacy(Metric) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] Metric
```
