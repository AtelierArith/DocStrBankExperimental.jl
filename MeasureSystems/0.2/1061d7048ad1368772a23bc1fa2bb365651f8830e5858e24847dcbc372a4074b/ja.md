```Julia
MetricArcsecond = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^7*𝟑^4*3/τ)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

標準の `MetricArcsecond` システムは、正確な `molarmass` と `vacuumpermeability` に基づいています。

```Julia
julia> boltzmann(MetricArcsecond) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] MetricArcsecond

julia> planckreduced(MetricArcsecond) # J⋅s⋅asec⁻¹
𝘩⋅2⁻⁷3⁻⁴5⁻³ = 5.112708449074074×10⁻⁴⁰ [J⋅s⋅asec⁻¹] MetricArcsecond

julia> lightspeed(MetricArcsecond) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MetricArcsecond

julia> vacuumpermeability(MetricArcsecond) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] MetricArcsecond

julia> electronmass(MetricArcsecond) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] MetricArcsecond

julia> molarmass(MetricArcsecond) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] MetricArcsecond

julia> luminousefficacy(MetricArcsecond) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] MetricArcsecond
```
