```Julia
MetricDegree = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^3*𝟑^2*𝟓/τ)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

標準の `MetricDegree` システムは、正確な `molarmass` と `vacuumpermeability` に基づいています。

```Julia
julia> boltzmann(MetricDegree) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 1.38064899953(43) × 10⁻²³ [J⋅K⁻¹] MetricDegree

julia> planckreduced(MetricDegree) # J⋅s⋅deg⁻¹
𝘩⋅2⁻³3⁻²5⁻¹ = 1.8405750416666666×10⁻³⁶ [J⋅s⋅deg⁻¹] MetricDegree

julia> lightspeed(MetricDegree) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] MetricDegree

julia> vacuumpermeability(MetricDegree) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷ = 1.2566370614359173×10⁻⁶ [H⋅m⁻¹] MetricDegree

julia> electronmass(MetricDegree) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg] MetricDegree

julia> molarmass(MetricDegree) # kg⋅mol⁻¹
2⁻³5⁻³ = 0.001 [kg⋅mol⁻¹] MetricDegree

julia> luminousefficacy(MetricDegree) # lm⋅W⁻¹
Kcd = 683.01969009009 [lm⋅W⁻¹] MetricDegree
```
