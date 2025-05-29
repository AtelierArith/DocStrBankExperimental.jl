```Julia
statcoulomb(U::UnitSystem) = charge(𝟏,U,ESU)
```

Electrostatic unit of `charge` (C).

```Julia
julia> statcoulomb(Metric) # C
3.3356409519815207e-10

julia> statcoulomb(EMU) # abC
3.33564095198152e-11

julia> statcoulomb(ESU) # statC
1
```
