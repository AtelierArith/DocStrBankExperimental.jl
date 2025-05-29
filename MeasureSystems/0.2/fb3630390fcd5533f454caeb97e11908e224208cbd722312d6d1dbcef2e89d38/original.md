```Julia
IAUJ = EntropySystem(Metric,DAY,JD,GMJ/G)
F=MLT⁻², M=M, L=L, T=T, Q=Q, Θ=Θ, N=N, J=J, A=𝟙, R=𝟙, C=𝟙
```

Astronomical (Jupiter) `UnitSystem` defined by `jupiterdistance` around the `solarmass`.

```Julia
julia> boltzmann(IAUJ) # MJ⋅JD²⋅D⁻²⋅K⁻¹
kB⋅NA⋅𝘩²R∞⋅α⁻²μₑᵤ⁻¹mP⁻²GMJ⁻¹τ⁻¹2⁶3⁴5⁻⁵/67336617049 = 8.95968(20) × 10⁻⁶⁵ [MJ⋅JD²D⁻²K⁻¹] IAUJ

julia> planckreduced(IAUJ) # MJ⋅JD²⋅D⁻¹⋅rad⁻¹
𝘩²𝘤⋅mP⁻²GMJ⁻¹τ⁻²2⁻⁵3⋅5⁻¹⁰/67336617049 = 7.92084(17) × 10⁻⁸¹ [MJ⋅JD²D⁻¹] IAUJ

julia> lightspeed(IAUJ) # JD⋅D⁻¹
𝘤⋅2⋅3²5⁻⁴/259493 = 33.272661653300865 [JD⋅D⁻¹] IAUJ

julia> vacuumpermeability(IAUJ) # MJ⋅JD²⋅C⁻²
𝘩⋅𝘤⋅mP⁻²GMJ⁻¹2⁻¹²3⁻¹5⁻¹³/259493 = 8.50430(19) × 10⁻⁴⁶ [MJ⋅JD⋅C⁻²] IAUJ

julia> electronmass(IAUJ) # MJ
𝘩²R∞⋅α⁻²mP⁻²GMJ⁻¹τ⁻¹2 = 4.79915(11) × 10⁻⁵⁸ [MJ] IAUJ

julia> molarmass(IAUJ) # MJ⋅mol⁻¹
𝘩⋅𝘤⋅mP⁻²GMJ⁻¹τ⁻¹2⁻³5⁻³ = 5.26836(12) × 10⁻³¹ [MJ⋅mol⁻¹] IAUJ

julia> luminousefficacy(IAUJ) # lm⋅D³⋅MJ⁻¹⋅JD⁻²
𝘩⁻¹𝘤⁻¹Kcd⋅mP²GMJ⋅τ⋅2⁻⁹3⁻⁷5⁶⋅67336617049 = 1.218177(27) × 10³⁹ [MJ⁻¹JD⁻²D³lm] IAUJ

julia> sqrt(gravitation(IAUJ)*solarmass(IAUJ)/jupiterdistance(IAUJ)^3) # D⁻¹
au³ᐟ²kG⋅τ⋅2⁻¹⁶3⁻¹¹ᐟ²5⁻¹²/1.3218691602384917×10⁸ = 0.001449102839405(44) [D⁻¹] IAUJ
```
