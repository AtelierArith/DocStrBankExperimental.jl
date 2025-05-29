```Julia
jupiterdistance(U::UnitSystem) = length(𝟏,U,IAUJ)
```

Standard distance between the Sun and the planet Jupiter (m or ft).

```Julia
julia> jupiterdistance(Metric) # m
7.784789999999999e11

julia> jupiterdistance(IAU) # au
5.203810698356415

julia> jupiterdistance(Metric)/lightspeed(Metric) # s
2596.726432657622
```
