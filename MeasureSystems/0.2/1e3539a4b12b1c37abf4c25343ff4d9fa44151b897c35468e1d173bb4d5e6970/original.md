```Julia
MetricGradian = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^4*𝟓^2/τ)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

Standard `MetricGradian` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(MetricGradian) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] MetricGradian

julia> planckreduced(MetricGradian) # J⋅s⋅gon⁻¹
𝘩⋅2⁻⁴5⁻² = 1.6565175375000004×10⁻³⁶ [J⋅s⋅gon⁻¹] MetricGradian

julia> lightspeed(MetricGradian) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MetricGradian

julia> vacuumpermeability(MetricGradian) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] MetricGradian

julia> electronmass(MetricGradian) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] MetricGradian

julia> molarmass(MetricGradian) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] MetricGradian

julia> luminousefficacy(MetricGradian) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] MetricGradian
```
