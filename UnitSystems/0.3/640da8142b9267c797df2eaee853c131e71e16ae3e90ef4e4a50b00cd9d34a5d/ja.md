```Julia
molality(U::UnitSystem,S::UnitSystem) = molarmass(U)/molarmass(S)
molality(v::Real,U::UnitSystem,S::UnitSystem) = v/molality(U,S)
```

モラルティまたは `mole` あたりの `mass` (mol⋅kg⁻¹)、単位換算係数。

```Julia
julia> molality(CGS,Metric) # kg⋅g⁻¹
1000.0

julia> molality(Metric,SI2019) # mol⋅mol⁻¹
1.000000000343744
```
