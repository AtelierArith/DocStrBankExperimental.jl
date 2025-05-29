```Julia
ESU = GaussSystem(Metric,(𝟏𝟎*𝘤)^-2,𝟐*τ)
```

Centimetre-gram-second `UnitSystem` variant based on `ESU` (non-rationalized).

```Julia
julia> boltzmann(ESU) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(ESU) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(ESU) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(ESU) # statH⋅cm⁻¹
1.1126500560536182e-21

julia> electronmass(ESU) # g
9.109383701558256e-28

julia> molarmass(ESU) # g⋅mol⁻¹
1

julia> luminousefficacy(ESU) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(ESU)
12.566370614359172
```
