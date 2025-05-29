```Julia
permittivity(U::UnitSystem,S::UnitSystem) = capacitance(U,S)*rationalization(U,S)/length(U,S)
permittivity(v::Real,U::UnitSystem,S::UnitSystem) = v/permittivity(U,S)
```

絶対的な `permittivity` または `capacitance` あたりの `length` (F⋅m⁻¹)、単位変換係数。

```Julia
julia> permittivity(EMU,Metric) # F⋅cm⋅abF⁻¹⋅m⁻¹
7.957747154594766e9

julia> permittivity(ESU,Metric) # F⋅m⁼¹
8.854187817620386e-12

julia> permittivity(Metric,SI2019) # F⋅F⁻¹
0.9999999994547903
```
