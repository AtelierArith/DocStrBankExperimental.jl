```Julia
polestrength(U::UnitSystem,S::UnitSystem) = magneticdipolemoment(U,S)/length(U,S)
polestrength(v::Real,U::UnitSystem,S::UnitSystem) = v/polestrength(U,S)
```

磁気 `polestrength` は `charge` (A⋅m) に類似しており、単位変換係数です。

```Julia
julia> polestrength(EMU,Metric) # A⋅m⋅pole⁻¹
0.10000000000000002

julia> polestrength(Metric,SI2019) # A⋅A⁻¹⋅
0.9999999997273952
```
