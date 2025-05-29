```Julia
MetricTurn = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟏/τ)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

Standard `MetricTurn` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(MetricTurn) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] MetricTurn

julia> planckreduced(MetricTurn) # J⋅s⋅τ⁻¹
𝘩 = 6.62607015×10⁻³⁴ [J⋅s⋅τ⁻¹] MetricTurn

julia> lightspeed(MetricTurn) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MetricTurn

julia> vacuumpermeability(MetricTurn) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] MetricTurn

julia> electronmass(MetricTurn) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] MetricTurn

julia> molarmass(MetricTurn) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] MetricTurn

julia> luminousefficacy(MetricTurn) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] MetricTurn
```
