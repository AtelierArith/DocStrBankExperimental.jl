```Julia
Gauss = GaussSystem(Metric,𝟏,𝟐*τ,𝟏𝟎^-2/𝘤)
```

Centimetre-gram-second `UnitSystem` variant `CGS` (Gauss-Lorentz, non-rationalized).

```Julia
julia> boltzmann(Gauss) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(Gauss) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(Gauss) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(Gauss) # statH⋅cm⁻¹
1

julia> electronmass(Gauss) # g
9.109383701558256e-28

julia> molarmass(Gauss) # g⋅mol⁻¹
1

julia> luminousefficacy(Gauss) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(Gauss)
12.566370614359172

julia> lorentz(Gauss)
3.335640951981521e-11
```
