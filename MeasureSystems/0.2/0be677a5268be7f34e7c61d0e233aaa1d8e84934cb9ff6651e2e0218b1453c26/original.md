```Julia
IPS = RankineSystem(Metric,ft/𝟐^2/𝟑,lb*g₀*𝟐^2*𝟑/ft)
F=F, M=FL⁻¹T², L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

British Gravitational `UnitSystem` historically used in the United States of America.

```Julia
julia> boltzmann(IPS) # in⋅lb⋅°R⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ft⁻¹lb⁻¹2⁶3⁻¹5⁴ = 6.7887629566(21) × 10⁻²³ [lb⋅in⋅°R⁻¹] IPS

julia> planckreduced(IPS) # in⋅lb⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹ft⁻¹lb⁻¹τ⁻¹2²3 = 9.333747076683978×10⁻³⁴ [lb⋅in⋅s] IPS

julia> lightspeed(IPS) # in⋅s⁻¹
𝘤⋅ft⁻¹2²3 = 1.1802852677165354×10¹⁰ [in⋅s⁻¹] IPS

julia> vacuumpermeability(IPS) # slinch⋅in⋅C⁻²
g₀⁻¹lb⁻¹τ⋅2⁻⁶5⁻⁷ = 2.8250324964133447×10⁻⁷ [lb⋅s²C⁻²] IPS

julia> electronmass(IPS) # slinch
𝘩⋅𝘤⁻¹R∞⋅α⁻²g₀⁻¹ft⋅lb⁻¹2⁻¹3⁻¹ = 5.2015921425(16) × 10⁻³³ [slinch] IPS

julia> molarmass(IPS) # slinch⋅slinch-mol⁻¹
𝟏 = 1.0 [slinch-slinch-mol⁻¹] IPS

julia> luminousefficacy(IPS) # lm⋅s⋅in⁻¹⋅lb⁻¹
Kcd⋅g₀⋅ft⋅lb⋅2⁻²3⁻¹ = 77.17086290732456 [lb⁻¹in⁻¹s⋅lm] IPS
```
