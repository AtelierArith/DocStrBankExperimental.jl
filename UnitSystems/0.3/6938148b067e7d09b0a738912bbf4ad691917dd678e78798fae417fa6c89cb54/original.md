```Julia
LorentzHeaviside = GaussSystem(Metric,𝟏,𝟏,centi/𝘤)
```

Centimetre-gram-second `UnitSystem` variant `HLU` (Heaviside-Lorentz, rationalized).

```Julia
julia> boltzmann(LorentzHeaviside) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(LorentzHeaviside) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(LorentzHeaviside) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(HLU) # hlH⋅cm⁻¹
1

julia> electronmass(LorentzHeaviside) # g
9.109383701558256e-28

julia> molarmass(LorentzHeaviside) # g⋅mol⁻¹
1

julia> luminousefficacy(LorentzHeaviside) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(LorentzHeaviside)
1

julia> lorentz(LorentzHeaviside)
3.335640951981521e-11
```
