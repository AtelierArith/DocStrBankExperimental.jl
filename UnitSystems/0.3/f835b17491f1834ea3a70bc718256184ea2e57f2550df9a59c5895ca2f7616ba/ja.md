```Julia
specificsusceptibility(U::UnitSystem,S::UnitSystem) = susceptibility(U,S)/density(U,S)
specificsusceptibility(v::Real,U::UnitSystem,S::UnitSystem) = v/specificsusceptibility(U,S)
```

磁気/電気質量の特定の `感受性` (m³⋅kg⁻¹)、単位変換係数。

```Julia
julia> specificsusceptibility(EMU,Metric) # m³⋅g⋅kg⁻¹⋅cm⁻³
0.01256637061435918

julia> specificsusceptibility(ESU,Metric) # m³⋅g⋅kg⁻¹⋅cm⁻³
0.01256637061435918

julia> specificsusceptibility(Metric,SI2019) # m³⋅kg⋅kg⁻¹⋅m⁻³
1
```
