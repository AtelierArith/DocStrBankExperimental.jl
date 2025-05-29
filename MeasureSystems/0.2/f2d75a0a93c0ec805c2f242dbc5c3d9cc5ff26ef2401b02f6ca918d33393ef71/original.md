```Julia
British = RankineSystem(Metric,ft,slug)
F=F, M=FL⁻¹T², L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

British Gravitational `UnitSystem` historically used by Britain and United States.

```Julia
julia> boltzmann(British) # ft⋅lb⋅°R⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ft⁻¹lb⁻¹2⁴3⁻²5⁴ = 5.6573024638(17) × 10⁻²⁴ [lb⋅ft⋅°R⁻¹] British

julia> planckreduced(British) # ft⋅lb⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹ft⁻¹lb⁻¹τ⁻¹ = 7.778122563903315×10⁻³⁵ [lb⋅ft⋅s] British

julia> lightspeed(British) # ft⋅s⁻¹
𝘤⋅ft⁻¹ = 9.835710564304461×10⁸ [ft⋅s⁻¹] British

julia> vacuumpermeability(British) # slug⋅ft⋅C⁻²
g₀⁻¹lb⁻¹τ⋅2⁻⁶5⁻⁷ = 2.8250324964133447×10⁻⁷ [lb⋅s²C⁻²] British

julia> electronmass(British) # slugs
𝘩⋅𝘤⁻¹R∞⋅α⁻²g₀⁻¹ft⋅lb⁻¹2 = 6.2419105710(19) × 10⁻³² [slug] British

julia> molarmass(British) # slug⋅slug-mol⁻¹
𝟏 = 1.0 [slug⋅slug-mol⁻¹] British

julia> luminousefficacy(British) # lm⋅s⋅ft⁻¹⋅lb⁻¹
Kcd⋅g₀⋅ft⋅lb = 926.0503548878947 [lb⁻¹ft⁻¹s⋅lm] British
```
