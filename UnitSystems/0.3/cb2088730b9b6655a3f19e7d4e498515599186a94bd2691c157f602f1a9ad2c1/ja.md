```Julia
jupiterdistance(U::UnitSystem) = length(𝟏,U,IAUJ)
```

太陽と惑星ジュピターの標準距離 (m または ft)。

```Julia
julia> jupiterdistance(Metric) # m
7.784789999999999e11

julia> jupiterdistance(IAU) # au
5.203810698356415

julia> jupiterdistance(Metric)/lightspeed(Metric) # s
2596.726432657622
```
