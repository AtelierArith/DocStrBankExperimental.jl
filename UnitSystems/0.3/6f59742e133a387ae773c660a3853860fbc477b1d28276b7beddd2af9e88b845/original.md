```Julia
abampere(U::UnitSystem) = current(𝟏,U,EMU)
```

Electromagnetic unit of `current` (C⋅s⁻¹).

```Julia
julia> abampere(Metric) # C⋅s⁻¹
10.0

julia> abampere(EMU) # abC⋅s⁻¹
1

julia> abampere(ESU) # statC⋅s⁻¹
2.9979245800000004e10
```
