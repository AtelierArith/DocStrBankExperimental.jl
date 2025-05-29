```Julia
specificmagnetization(U::UnitSystem,S::UnitSystem) = magneticmoment(U,S)/mass(U,S)
specificmagnetization(v::Real,U::UnitSystem,S::UnitSystem) = v/specificmagnetization(U,S)
```

`mass`あたりの`magneticmoment`の量（Wb⋅m⋅kg⁻¹）、単位変換係数。

```Julia
julia> specificmagnetization(EMU,Metric) # Wb⋅m⋅g⋅Mx⁻¹⋅cm⁻¹⋅kg⁻¹
1.0e7

julia> specificmagnetization(ESU,Metric) # Wb⋅m⋅g⋅statWb⁻¹⋅cm⁻¹⋅kg⁻¹
0.000333564095198152

julia> specificmagnetization(Metric,SI2019) # Wb⋅Wb⁻¹
0.9999999997273952
```
