```Julia
English = RankineSystem(Metric,ft,lb,g₀/ft)
F=F, M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=A, R=𝟙, C=𝟙
```

アメリカ合衆国で歴史的に使用されている英語工学 `UnitSystem`。

```Julia
julia> boltzmann(English) # ft⋅lbf⋅°R⁻¹
kB⋅NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹g₀⁻¹ft⁻¹lb⁻¹2⁴3⁻²5⁴ = 5.6573024638(17) × 10⁻²⁴ [lbf⋅ft⋅°R⁻¹] English

julia> planckreduced(English) # ft⋅lbf⋅s⋅rad⁻¹
𝘩⋅g₀⁻¹ft⁻¹lb⁻¹τ⁻¹ = 7.778122563903315×10⁻³⁵ [lbf⋅ft⋅s⋅rad⁻¹] English

julia> lightspeed(English) # ft⋅s⁻¹
𝘤⋅ft⁻¹ = 9.835710564304461×10⁸ [ft⋅s⁻¹] English

julia> vacuumpermeability(English) # lbm⋅ft⋅C⁻²
g₀⁻¹lb⁻¹τ⋅2⁻⁶5⁻⁷ = 2.8250324964133447×10⁻⁷ [lbf⋅s²C⁻²] English

julia> electronmass(English) # lbm
𝘩⋅𝘤⁻¹R∞⋅α⁻²lb⁻¹2 = 2.00827533796(62) × 10⁻³⁰ [lbm] English

julia> molarmass(English) # lbm⋅lb-mol⁻¹
𝟏 = 1.0 [lbm⋅lb-mol⁻¹] English

julia> luminousefficacy(English) # lm⋅s⋅ft⁻¹⋅lbf⁻¹
Kcd⋅g₀⋅ft⋅lb = 926.0503548878947 [lbf⁻¹ft⁻¹s⋅lm] English

julia> gravity(English) # lbm⋅ft⋅lbf⁻¹⋅s⁻²
g₀⋅ft⁻¹ = 32.17404855643044 [lbf⁻¹lbm⋅ft⋅s⁻²] English
```
