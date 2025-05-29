```Julia
ampere(U::UnitSystem) = current(𝟏,U,Metric)
```

Metric unit of `current` (C⋅s⁻¹).

```Julia
julia> ampere(Metric) # C⋅s⁻¹
1

julia> ampere(EMU) # abC⋅s⁻¹
0.1

julia> ampere(ESU) # statC⋅s⁻¹
2.9979245800000005e9
```
