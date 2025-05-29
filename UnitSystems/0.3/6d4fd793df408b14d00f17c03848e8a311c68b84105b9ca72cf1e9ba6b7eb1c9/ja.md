```Julia
kilogram(U::UnitSystem) = mass(𝟏,U,Metric)
```

メトリック `kilogram` 単位の `mass` (kg または lb)。

```Julia
julia> kilogram(Metric) # kg
1

julia> kilogram(CGS) # g
1000.0

julia> kilogram(English) # lb
2.2046226218487757

julia> kilogram(British) # slug
0.06852176585679176

julia> kilogram(Gravitational) # hyl
0.10197162129779283
```
