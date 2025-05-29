```Julia
energy(U::UnitSystem,S::UnitSystem) = mass(U,S)*specificenergy(U,S)
energy(v::Real,U::UnitSystem,S::UnitSystem) = v/energy(U,S)
```

仕事または熱または `energy` (J, N⋅m, kg⋅m²⋅s⁻²)、単位換算係数。

```Julia
julia> energy(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> energy(CGS,English) # ft⋅lb⋅erg⁻¹
7.375621492772652e-8

julia> energy(English,Metric) # J⋅ft⁻¹⋅lb⁻¹
1.3558179483314003

julia> 0.001/3600 # J⋅kW⁻¹⋅h⁻¹
2.7777777777777776e-7

julia> 1/elementarycharge(SI2019) # J⋅eV⁻¹
6.241509074460763e18
```
