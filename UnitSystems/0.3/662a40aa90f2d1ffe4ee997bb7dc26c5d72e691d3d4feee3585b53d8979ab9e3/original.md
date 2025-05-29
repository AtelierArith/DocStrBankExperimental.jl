```Julia
English = RankineSystem(Metric,ft,lb,g₀/ft)
```

English Engineering `UnitSystem` historically used in the United States of America.

```Julia
julia> boltzmann(English) # ft⋅lbf⋅°R⁻¹
5.657302463819266e-24

julia> planckreduced(English) # ft⋅lbf⋅s⋅rad⁻¹
7.778122563903315e-35

julia> lightspeed(English) # ft⋅s⁻¹
9.835710564304461e8

julia> vacuumpermeability(English) # lbm⋅ft⋅C⁻²
2.8250324964133447e-7

julia> electronmass(English) # lbm
2.0082753379555867e-30

julia> molarmass(English) # lbm⋅lb-mol⁻¹
1

julia> luminousefficacy(English) # lm⋅s⋅ft⁻¹⋅lbf⁻¹
926.0503548878946

julia> gravity(English) # lbm⋅ft⋅lbf⁻¹⋅s⁻²
32.17404855643044
```
