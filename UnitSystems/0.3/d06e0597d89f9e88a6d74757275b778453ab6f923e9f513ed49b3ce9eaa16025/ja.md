```Julia
IAU☉ = EntropySystem(Metric,DAY,au,GM☉/G)
```

国際天文学連合によって定義された太陽の `UnitSystem` と `solarmass`。

```Julia
julia> boltzmann(IAU) # M⊙⋅au²⋅D⁻²⋅K⁻¹
2.3160832669610065e-66

julia> planckreduced(IAU) # M⊙⋅au²⋅D⁻¹⋅rad⁻¹
2.047544291551459e-82

julia> lightspeed(IAU) # au⋅D⁻¹
173.14463267424034

julia> vacuumpermeability(IAU) # M⊙⋅au²⋅C⁻²
4.224532713546819e-48

julia> electronmass(IAU) # M⊙
4.581241868792794e-61

julia> molarmass(IAU) # M☉⋅mol⁻¹
5.029145789532528e-34

julia> luminousefficacy(IAU) # lm⋅D³⋅M☉⁻¹⋅au⁻²
4.712469960476774e40

julia> gaussgravitation(IAU) # D⁻¹
0.017202098964713468
```
