```Julia
molarconductivity(U::UnitSystem,S::UnitSystem) = conductivity(U,S)*area(U,S)/molaramount(U,S)
molarconductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/molarconductivity(U,S)
```

`molarvolume`あたりの導電率または`molarconductivity` (S⋅m²⋅mol⁻¹)、単位変換係数。

```Julia
julia> molarconductivity(EMU,Metric) # S⋅m²⋅abΩ⋅cm⁻²
1.0000000000000004e7

julia> molarconductivity(ESU,Metric) # S⋅m²⋅statΩ⋅cm⁻²
1.1126500560536184e-14
```
