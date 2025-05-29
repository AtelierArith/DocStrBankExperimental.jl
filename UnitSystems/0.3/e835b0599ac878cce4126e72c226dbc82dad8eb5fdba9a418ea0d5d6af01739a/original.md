```Julia
charge(U::UnitSystem,S::UnitSystem) = sqrt(action(U,S)*current(U,S)/electricpotential(U,S))
charge(v::Real,U::UnitSystem,S::UnitSystem) = v/charge(U,S)
```

Electric `charge` quantization (C, A⋅s), unit conversion factor.

```Julia
julia> charge(EMU,Metric) # C⋅abC⁻¹
10.0

julia> charge(EMU,ESU) # stC⋅abC⁻¹
2.9979245800000004e10

julia> charge(ESU,Metric) # C⋅stC⁻¹
3.33564095198152e-10

julia> charge(Metric,SI2019) # C⋅C⁻¹
0.9999999997273952

julia> charge(Hartree,SI2019) # C⋅𝘦⁻¹
1.6021766340000001e-19
```
