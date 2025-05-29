```Julia
molarentropy(U::UnitSystem,S::UnitSystem) = entropy(U,S)/molaramount(U,S)
molarentropy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarentropy(U,S)
```

モル熱容量または `molaramount` あたりの `entropy` (J⋅K⁻¹⋅mol⁻¹)、単位換算係数。

```Julia
julia> molarentropy(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> molarentropy(English,SI2019) # J⋅°R⋅lb-mol⋅ft⁻¹⋅lb⁻¹⋅K⁻¹⋅mol⁻¹
0.005380320455999999
```
