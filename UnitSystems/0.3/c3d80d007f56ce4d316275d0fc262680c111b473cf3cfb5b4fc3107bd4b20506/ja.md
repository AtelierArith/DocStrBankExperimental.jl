```Julia
statvolt(U::UnitSystem) = electricpotential(𝟏,U,ESU)
```

静電単位の `electricpotential` (V)。

```Julia
julia> statvolt(Metric) # V
299.792458

julia> statvolt(EMU) # abV
2.9979245800000004e10

julia> statvolt(ESU) # statV
1
```
