```Julia
current(U::UnitSystem,S::UnitSystem) = charge(U,S)/time(U,S)
current(v::Real,U::UnitSystem,S::UnitSystem) = v/current(U,S)
```

Flow of electric `charge` per `time` or `current` (A, C⋅s⁻¹), unit conversion factor.

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
