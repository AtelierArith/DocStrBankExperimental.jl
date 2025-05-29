```Julia
International = ElectricSystem(Metric,Ωᵢₜ = 1.000495,Vᵢₜ = 1.00033)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

International `UnitSystem` with United States measurements of `Ωᵢₜ` and `Vᵢₜ`.

```Julia
julia> resistance(International,Metric) # Ω⋅Ω⁻¹
Ωᵢₜ = 1.000495 [kg⋅m⋅s⁻²C⁻²]/[kg⋅m⋅s⁻²C⁻²] International -> Metric

julia> electricpotential(International,Metric) # V⋅V⁻¹
Vᵢₜ = 1.00033 [V⋅m⁻¹]/[V⋅m⁻¹] International -> Metric

julia> boltzmann(International) # J⋅K⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹Ωᵢₜ⋅Vᵢₜ⁻²2⁴5³ = 1.38042119247(42) × 10⁻²³ [J⋅K⁻¹] International

julia> planckreduced(International) # J⋅s⋅rad⁻¹
𝘩⋅Ωᵢₜ⋅Vᵢₜ⁻²τ⁻¹ = 1.0543978133151816×10⁻³⁴ [J⋅s] International

julia> lightspeed(International) # m⋅s⁻¹
𝘤 = 2.99792458×10⁸ [m⋅s⁻¹] International

julia> vacuumpermeability(International) # H⋅m⁻¹
Ωᵢₜ⁻¹τ⋅2⁻⁶5⁻⁷ = 1.2560153338456637×10⁻⁶ [H⋅m⁻¹] International

julia> electronmass(International) # kg
𝘩⋅𝘤⁻¹R∞⋅α⁻²Ωᵢₜ⋅Vᵢₜ⁻²2 = 9.1078806534(28) × 10⁻³¹ [kg] International

julia> molarmass(International) # kg⋅mol⁻¹
Ωᵢₜ⋅Vᵢₜ⁻²2⁻³5⁻³ = 0.0009998350000179567 [kg⋅mol⁻¹] International

julia> luminousefficacy(International) # lm⋅W⁻¹
Kcd⋅Ωᵢₜ⁻¹Vᵢₜ² = 683.1324069249656 [lm⋅W⁻¹] International
```
