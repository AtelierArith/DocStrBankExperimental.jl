```Julia
statampere(U::UnitSystem) = current(𝟏,U,ESU)
```

Electrostatic unit of `current` (C⋅s⁻¹).

```Julia
julia> statampere(Metric) # C⋅s⁻¹
3.3356409519815207e-10

julia> statampere(EMU) # abC⋅s⁻¹
3.33564095198152e-11

julia> statampere(ESU) # statC⋅s⁻¹
1
```
