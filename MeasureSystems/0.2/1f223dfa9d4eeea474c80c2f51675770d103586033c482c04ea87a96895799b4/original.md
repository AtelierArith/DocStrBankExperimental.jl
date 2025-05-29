```Julia
Survey = RankineSystem(Metric,ftUS,lb,g₀/ftUS)
F=F, M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

English Engineering `UnitSystem` based on the geophysical US survey foot (1200/3937).

```Julia
julia> boltzmann(Survey) # ftUS⋅lbf⋅°R⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ftUS⁻¹lb⁻¹2⁴3⁻²5⁴ = 5.6572911492(17) × 10⁻²⁴ [lbf⋅ft⋅°R⁻¹] Survey

julia> planckreduced(Survey) # ftUS⋅lbf⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹ftUS⁻¹lb⁻¹τ⁻¹ = 7.77810700765819×10⁻³⁵ [lbf⋅ft⋅s⋅rad⁻¹] Survey

julia> lightspeed(Survey) # ftUS⋅s⁻¹
𝘤⋅ftUS⁻¹ = 9.835690892883334×10⁸ [ft⋅s⁻¹] Survey

julia> vacuumpermeability(Survey) # lbm⋅ftUS⋅C⁻²
g₀⁻¹lb⁻¹τ⋅2⁻⁶5⁻⁷ = 2.8250324964133447×10⁻⁷ [lbf⋅s²C⁻²] Survey

julia> electronmass(Survey) # lbm
𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹2 = 2.00827533796(62) × 10⁻³⁰ [lbm] Survey

julia> molarmass(Survey) # lbm⋅lb-mol⁻¹
𝟏 = 1.0 [lbm⋅lb-mol⁻¹] Survey

julia> luminousefficacy(Survey) # lm⋅s⋅ft⁻¹⋅lbf⁻¹
Kcd⋅g₀⋅ftUS⋅lb = 926.0522069923087 [lbf⁻¹ft⁻¹s⋅lm] Survey

julia> gravity(Survey) # lbm⋅ftUS⋅lbf⁻¹⋅s⁻²
g₀⋅ftUS⁻¹ = 32.17398420833334 [lbf⁻¹lbm⋅ft⋅s⁻²] Survey
```
