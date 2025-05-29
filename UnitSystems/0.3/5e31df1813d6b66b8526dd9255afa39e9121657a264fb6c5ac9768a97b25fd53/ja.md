```Julia
molarmass(U::UnitSystem,S::UnitSystem) = molarmass(S)/molarmass(U)
molarmass(v::Real,U::UnitSystem,S::UnitSystem) = v/molarmass(U,S)
```

モル質量または `質量` あたり `モル` (kg⋅mol⁻¹)、単位変換係数。

```Julia
julia> molarmass(CGS,Metric) # kg⋅g⁻¹
0.001

julia> molarmass(Metric,SI2019) # mol⋅mol⁻¹
0.9999999996562561
```
