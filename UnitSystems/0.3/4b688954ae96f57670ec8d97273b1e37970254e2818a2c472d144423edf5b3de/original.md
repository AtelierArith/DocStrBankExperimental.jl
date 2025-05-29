```Julia
abvolt(U::UnitSystem) = electricpotential(𝟏,U,EMU)
```

Electromagnetic unit of `electricpotential` (V).

```Julia
julia> abvolt(Metric) # V
9.999999999999999e-9

julia> abvolt(EMU) # abV
1

julia> abvolt(ESU) # statV
3.33564095198152e-11
```
