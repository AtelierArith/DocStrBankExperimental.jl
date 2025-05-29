```Julia
molarsusceptibility(U::UnitSystem,S::UnitSystem) = specificsusceptibility(U,S)*molarmass(U,S)
molarsusceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/molarsusceptibility(U,S)
```

磁気/電気モル質量 `susceptibility` (m³⋅mol⁻¹)、単位変換係数。

```Julia
julia> molarsusceptibility(CGS,Metric) # m³⋅cm⁻³
1.256637061435918e-5

julia> molarsusceptibility(Metric,SI2019) # m³⋅mol⋅mol⁻¹⋅cm⁻³
0.9999999996562561
```
