```Julia
IAUE = EntropySystem(Metric,DAY,LD,GME/G)
```

Astronomical (Earth) `UnitSystem` defined by `lunardistance` around the `earthmass`.

```Julia
julia> boltzmann(IAUE) # ME⋅LD²⋅D⁻²⋅K⁻¹
1.1679233837035083e-55

julia> planckreduced(IAUE) # ME⋅LD²⋅D⁻¹⋅rad⁻¹
1.0325081534781642e-71

julia> lightspeed(IAUE) # LD⋅D⁻¹
67383.2876027253

julia> vacuumpermeability(IAUE) # ME⋅LD²⋅C⁻²
5.473885382987154e-40

julia> electronmass(IAUE) # ME
1.5253063572240283e-55

julia> molarmass(IAUE) # ME⋅mol⁻¹
1.6744341957657449e-28

julia> luminousefficacy(IAUE) # lm⋅D³⋅ME⁻¹⋅LD⁻²
9.34519590395274e29

julia> turn(IAU)/gaussianmonth(IAU) # D⁻¹
0.22888074401572372
```
