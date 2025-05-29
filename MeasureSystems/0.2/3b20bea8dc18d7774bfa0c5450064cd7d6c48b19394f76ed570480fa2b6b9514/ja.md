```Julia
MetricArcminute = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^5*𝟑^3*𝟓^2/τ)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

標準の `MetricArcminute` システムは、正確な `molarmass` と `vacuumpermeability` に基づいています。

```Julia
julia> boltzmann(MetricArcminute) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] MetricArcminute

julia> planckreduced(MetricArcminute) # J⋅s⋅amin⁻¹
𝘩⋅2⁻⁵3⁻³5⁻² = 3.0676250694444446×10⁻³⁸ [J⋅s⋅amin⁻¹] MetricArcminute

julia> lightspeed(MetricArcminute) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MetricArcminute

julia> vacuumpermeability(MetricArcminute) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] MetricArcminute

julia> electronmass(MetricArcminute) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] MetricArcminute

julia> molarmass(MetricArcminute) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] MetricArcminute

julia> luminousefficacy(MetricArcminute) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] MetricArcminute
```
