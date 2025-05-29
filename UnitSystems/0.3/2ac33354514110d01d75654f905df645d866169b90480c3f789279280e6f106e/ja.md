```Julia
abmho(U::UnitSystem) = conductance(𝟏,U,EMU)
```

導電率の電磁単位 (S)。

```Julia
julia> abmho(Metric) # S
1.0000000000000001e9

julia> abmho(EMU) # abS
1

julia> abmho(ESU) # statS
8.987551787368178e20
```
