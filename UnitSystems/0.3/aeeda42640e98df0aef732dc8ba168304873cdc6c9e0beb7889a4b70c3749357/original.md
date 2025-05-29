```Julia
volt(U::UnitSystem) = electricpotential(𝟏,U,Metric)
```

Metric unit of `electricpotential` (V).

```Julia
julia> volt(Metric) # V
1

julia> volt(EMU) # abV
1.0e8

julia> volt(ESU) # statV
0.0033356409519815196
```
