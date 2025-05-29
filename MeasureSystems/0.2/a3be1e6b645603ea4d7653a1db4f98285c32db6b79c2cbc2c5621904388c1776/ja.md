```Julia
IAU☉ = EntropySystem(Metric,DAY,au,GM☉/G)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

国際天文学連合によって定義された太陽の `UnitSystem` と `solarmass`。

```Julia
julia> boltzmann(IAU) # M⊙⋅au²⋅D⁻²⋅K⁻¹
kB⋅NA⋅𝘩²R∞⋅α⁻²μₑᵤ⁻¹au⁻⁵kG⁻²mP⁻²τ⁻³2⁴⁶3²⁰5¹⁷ = 2.316083(51) × 10⁻⁶⁶ [M☉⋅au²D⁻²K⁻¹] IAU☉

julia> planckreduced(IAU) # M⊙⋅au²⋅D⁻¹⋅rad⁻¹
𝘩²𝘤⋅au⁻⁵kG⁻²mP⁻²τ⁻⁴2³⁵3¹⁷5¹² = 2.047544(45) × 10⁻⁸² [M☉⋅au²D⁻¹] IAU☉

julia> lightspeed(IAU) # au⋅D⁻¹
𝘤⋅au⁻¹2⁷3³5² = 173.1446326742(35) [au⋅D⁻¹] IAU☉

julia> vacuumpermeability(IAU) # M⊙⋅au²⋅C⁻²
𝘩⋅𝘤⋅au⁻⁴kG⁻²mP⁻²τ⁻²2²²3¹⁴5³ = 4.224533(93) × 10⁻⁴⁸ [M☉⋅au⋅C⁻²] IAU☉

julia> electronmass(IAU) # M⊙
𝘩²R∞⋅α⁻²au⁻³kG⁻²mP⁻²τ⁻³2²⁹3¹⁴5¹⁰ = 4.58124(10) × 10⁻⁶¹ [M☉] IAU☉

julia> molarmass(IAU) # M☉⋅mol⁻¹
𝘩⋅𝘤⋅au⁻³kG⁻²mP⁻²τ⁻³2²⁵3¹⁴5⁷ = 5.02915(11) × 10⁻³⁴ [M☉⋅mol⁻¹] IAU☉

julia> luminousefficacy(IAU) # lm⋅D³⋅M☉⁻¹⋅au⁻²
𝘩⁻¹𝘤⁻¹Kcd⋅au⁵kG²mP²τ³2⁻⁴⁹3⁻²³5⁻¹⁶ = 4.71247(10) × 10⁴⁰ [M☉⁻¹au⁻²D³lm] IAU☉

julia> gaussgravitation(IAU) # D⁻¹
kG⋅τ⋅2⁻⁷3⁻⁴5⁻³ = 0.017202098964713464 [D⁻¹] IAU☉
```
