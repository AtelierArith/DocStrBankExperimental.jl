```Julia
specificentropy(U::UnitSystem,S::UnitSystem) = specificenergy(U,S)/temperature(U,S)
specificentropy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificentropy(U,S)
```

Specific heat capacity or `specificentropy` (J⋅K⁻¹⋅kg⁻¹), unit conversion factor.

```Julia
julia> specificentropy(Metric,SI2019) # m²⋅K⋅K⁻¹⋅cm⁻²
1.000000000343744

julia> specificentropy(CGS,Metric) # m²⋅cm⁻²
0.0001

julia> specificentropy(English,Metric) # m²⋅°R⋅K⁻¹⋅ft⁻²
5.380320456

julia> specificentropy(Survey,English) # ft²⋅°R⋅ftUS⁻²⋅°R⁻¹
1.000002000004
```
