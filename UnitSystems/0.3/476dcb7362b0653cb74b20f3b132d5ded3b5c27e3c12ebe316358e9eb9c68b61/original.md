```Julia
molarsusceptibility(U::UnitSystem,S::UnitSystem) = specificsusceptibility(U,S)*molarmass(U,S)
molarsusceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/molarsusceptibility(U,S)
```

Magnetic/electric molar mass `susceptibility` (m³⋅mol⁻¹), unit conversion factor.

```Julia
julia> molarsusceptibility(CGS,Metric) # m³⋅cm⁻³
1.256637061435918e-5

julia> molarsusceptibility(Metric,SI2019) # m³⋅mol⋅mol⁻¹⋅cm⁻³
0.9999999996562561
```
