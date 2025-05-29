```Julia
abohm(U::UnitSystem) = resistance(𝟏,U,EMU)
```

電磁単位の `resistance` (Ω)。

```Julia
julia> abohm(Metric) # Ω
9.999999999999999e-10

julia> abohm(EMU) # abΩ
1

julia> abohm(ESU) # statΩ
1.1126500560536182e-21
```
