```Julia
specificentropy(U::UnitSystem,S::UnitSystem) = specificenergy(U,S)/temperature(U,S)
specificentropy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificentropy(U,S)
```

比熱容量または `specificentropy` (J⋅K⁻¹⋅kg⁻¹)、単位換算係数。

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
