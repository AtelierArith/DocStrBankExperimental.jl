```Julia
hyl(U::UnitSystem) = mass(𝟏,U,Gravitational)
```

重力メトリック `hyl` 単位の `mass` (kg または lb)。

```Julia
julia> hyl(Metric) # kg
9.80665

julia> hyl(CGS) # g
9806.65

julia> hyl(English) # lb
21.619962434553297

julia> hyl(British) # slug
0.6719689751395069

julia> hyl(Gravitational) # hyl
1
```
