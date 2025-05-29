```Julia
vacuumpermittivity(U::UnitSystem) = 𝟏/vacuumpermeability(U)/(lightspeed(U)*lorentz(U))^2
```

Dielectric permittivity constant `ε₀` of a classical vacuum (C²⋅N⁻¹⋅m⁻²).

```Julia
julia> vacuumpermittivity(Metric) # F⋅m⁻¹
8.854187817620389e-12

julia> vacuumpermittivity(Conventional) # F⋅m⁻¹
8.854187970341477e-12

julia> vacuumpermittivity(CODATA) # F⋅m⁻¹
8.854187814098007e-12

julia> vacuumpermittivity(SI2019) # F⋅m⁻¹
8.854187812792999e-12

julia> vacuumpermittivity(International) # F⋅m⁻¹
8.85857064059011e-12

julia> vacuumpermittivity(EMU) # abF⋅cm⁻¹
1.1126500560536184e-21

julia> vacuumpermittivity(ESU) # statF⋅cm⁻¹
1.0000000000000002

julia> vacuumpermittivity(SI2019)/elementarycharge(SI2019) # 𝘦²⋅eV⁻¹⋅m⁻¹
5.5263493580527395e7
```
