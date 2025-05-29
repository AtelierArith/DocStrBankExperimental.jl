```Julia
abhenry(U::UnitSystem) = inductance(𝟏,U,EMU)
```

Electromagnetic unit of `inductance` (H).

```Julia
julia> abhenry(Metric) # H
9.999999999999999e-10

julia> abhenry(EMU) # abH
1

julia> abhenry(ESU) # statH
1.1126500560536182e-21
```
