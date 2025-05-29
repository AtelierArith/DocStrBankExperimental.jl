```Julia
polestrength(U::UnitSystem,S::UnitSystem) = magneticdipolemoment(U,S)/length(U,S)
polestrength(v::Real,U::UnitSystem,S::UnitSystem) = v/polestrength(U,S)
```

Magnetic `polestrength` is analogous to `charge` (A⋅m), unit conversion factor.

```Julia
julia> polestrength(EMU,Metric) # A⋅m⋅pole⁻¹
0.10000000000000002

julia> polestrength(Metric,SI2019) # A⋅A⁻¹⋅
0.9999999997273952
```
