```Julia
abvolt(U::UnitSystem) = electricpotential(𝟏,U,EMU)
```

電磁単位の `electricpotential` (V)。

```Julia
julia> abvolt(Metric) # V
9.999999999999999e-9

julia> abvolt(EMU) # abV
1

julia> abvolt(ESU) # statV
3.33564095198152e-11
```
