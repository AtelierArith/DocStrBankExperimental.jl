```Julia
EMU = GaussSystem(Metric,𝟏,𝟐*τ)
```

Centimetre-gram-second `UnitSystem` variant based on `EMU` (non-rationalized).

```Julia
julia> boltzmann(EMU) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(EMU) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(EMU) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(EMU) # abH⋅cm⁻¹
1

julia> electronmass(EMU) # g
9.109383701558256e-28

julia> molarmass(EMU) # g⋅mol⁻¹
1

julia> luminousefficacy(EMU) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(EMU)
12.566370614359172
```
