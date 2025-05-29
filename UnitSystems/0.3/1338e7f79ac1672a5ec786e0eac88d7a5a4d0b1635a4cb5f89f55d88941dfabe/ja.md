```Julia
current(U::UnitSystem,S::UnitSystem) = charge(U,S)/time(U,S)
current(v::Real,U::UnitSystem,S::UnitSystem) = v/current(U,S)
```

電気の `charge` の流れを `time` あたり、または `current` (A, C⋅s⁻¹)、単位変換係数。

```Julia
julia> current(EMU,Metric) # A⋅Bi⁻¹
10.0

julia> current(EMU,ESU) # statA⋅Bi⁻¹
2.9979245800000004e10

julia> current(ESU,Metric) # A⋅statA⁻¹
3.33564095198152e-10

julia> current(Metric,SI2019) # A⋅A⁻¹
0.9999999997273952
```
