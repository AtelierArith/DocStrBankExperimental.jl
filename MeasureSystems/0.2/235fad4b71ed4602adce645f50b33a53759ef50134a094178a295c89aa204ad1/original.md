```Julia
InternationalMean = ElectricSystem(Metric,1.00049,1.00034)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

International `UnitSystem` with mean measurements of `Ωᵢₜ` and `Vᵢₜ`.

```Julia
julia> resistance(InternationalMean,Metric) # Ω⋅Ω⁻¹
1.00049 = 1.00049 [kg⋅m⋅s⁻²C⁻²]/[kg⋅m⋅s⁻²C⁻²] InternationalMean -> Metric

julia> electricpotential(InternationalMean,Metric) # V⋅V⁻¹
1.00034 = 1.00034 [V⋅m⁻¹]/[V⋅m⁻¹] InternationalMean -> Metric

julia> boltzmann(InternationalMean) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³/1.0001900224889804 = 1.38038669501(42) × 10⁻²³ [J⋅K⁻¹] InternationalMean

julia> planckreduced(InternationalMean) # J⋅s⋅rad⁻¹
𝘩⋅τ⁻¹/1.0001900224889804 = 1.0543714633563797×10⁻³⁴ [J⋅s] InternationalMean

julia> lightspeed(InternationalMean) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] InternationalMean

julia> vacuumpermeability(InternationalMean) # H⋅m⁻¹
τ⋅2⁻⁶5⁻⁷/1.00049 = 1.2560216108466022×10⁻⁶ [H⋅m⁻¹] InternationalMean

julia> electronmass(InternationalMean) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²2/1.0001900224889804 = 9.1076530427(28) × 10⁻³¹ [kg] InternationalMean

julia> molarmass(InternationalMean) # kg⋅mol⁻¹
2⁻³5⁻³/1.0001900224889804 = 0.0009998100136127059 [kg⋅mol⁻¹] InternationalMean

julia> luminousefficacy(International) # lm⋅W⁻¹
Kcd⋅Ωᵢₜ⁻¹Vᵢₜ² = 683.1324069249656 [lm⋅W⁻¹] International
```
