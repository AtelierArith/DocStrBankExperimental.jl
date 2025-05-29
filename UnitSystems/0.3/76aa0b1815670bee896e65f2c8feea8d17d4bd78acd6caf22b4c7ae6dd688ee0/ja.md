```Julia
ohm(U::UnitSystem) = resistance(𝟏,U,Metric)
```

抵抗のメトリック単位 (Ω)。

```Julia
julia> ohm(Metric) # Ω
1

julia> ohm(EMU) # abΩ
9.999999999999999e8

julia> ohm(ESU) # statΩ
1.112650056053618e-12
```
