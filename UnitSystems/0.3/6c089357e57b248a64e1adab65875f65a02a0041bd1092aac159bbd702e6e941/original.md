```Julia
Survey = RankineSystem(Metric,ftUS,lb,g₀/ftUS)
```

English Engineering `UnitSystem` based on the geophysical US survey foot (1200/3937).

```Julia
julia> boltzmann(Survey) # ftUS⋅lbf⋅°R⁻¹
5.65729114921434e-24

julia> planckreduced(Survey) # ftUS⋅lbf⋅s⋅rad⁻¹
7.778107007658189e-35

julia> lightspeed(Survey) # ftUS⋅s⁻¹
9.835690892883334e8

julia> vacuumpermeability(Survey) # lbm⋅ftUS⋅C⁻²
2.8250324964133457e-7

julia> electronmass(Survey) # lbm
2.0082753379555867e-30

julia> molarmass(Survey) # lbm⋅lb-mol⁻¹
1

julia> luminousefficacy(Survey) # lm⋅s⋅ft⁻¹⋅lbf⁻¹
926.0522069923085

julia> gravity(Survey) # lbm⋅ftUS⋅lbf⁻¹⋅s⁻²
32.17398420833333
```
