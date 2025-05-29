```Julia
magneticdipolemoment(U::UnitSystem,S::UnitSystem) = current(U,S)*lorentz(U,S)/area(U,S)/gravity(U,S)/angle(U,S)
magneticdipolemoment(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticdipolemoment(U,S)
```

磁気双極子モーメントまたは `magneticdipolemoment` (J⋅T⁻¹, A⋅m²)、単位変換係数。

```Julia
julia> magneticdipolemoment(EMU,Metric) # J⋅G⋅T⁻¹⋅erg⁻¹
0.0010000000000000005

julia> magneticdipolemoment(ESU,Metric) # J⋅statT⋅T⁻¹⋅erg⁼¹
3.3356409519815216e-14

julia> magneticdipolemoment(Metric,SI2019) # A⋅A⁻¹⋅
0.9999999997273952
```
