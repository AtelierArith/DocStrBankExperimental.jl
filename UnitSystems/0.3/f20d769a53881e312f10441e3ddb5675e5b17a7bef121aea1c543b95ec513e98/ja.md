```Julia
specificenergy(U::UnitSystem,S::UnitSystem) = speed(U,S)^2/gravity(U,S)
specificenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificenergy(U,S)
```

質量あたりのエネルギーまたは `energy` または `specificenergy` (J⋅kg⁻¹)、単位変換係数。

```Julia
julia> specificenergy(CGS,Metric) # m²⋅cm⁻²
0.0001

julia> specificenergy(IAU,Metric) # m²⋅day²⋅s⁻²⋅au⁻²
2.9979427777207e12

julia> specificenergy(English,Metric) # m²⋅ft⁻²
2.98906692

julia> specificenergy(Survey,English) # ft²⋅ftUS⁻²
1.000002000004
```
