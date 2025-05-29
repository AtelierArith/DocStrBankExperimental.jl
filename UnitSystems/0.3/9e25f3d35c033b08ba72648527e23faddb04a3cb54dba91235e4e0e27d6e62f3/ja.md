```Julia
statohm(U::UnitSystem) = resistance(𝟏,U,ESU)
```

静電単位の `resistance` (Ω)。

```Julia
julia> statohm(Metric) # Ω
8.987551787368176e11

julia> statohm(EMU) # abΩ
8.987551787368178e20

julia> statohm(ESU) # statΩ
1
```
