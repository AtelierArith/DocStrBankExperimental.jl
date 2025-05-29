```Julia
tonne(U::UnitSystem) = mass(𝟏,U,MTS)
```

Metric `tonne` unit of `mass` (kg or lb).

```Julia
julia> tonne(Metric) # kg
1000

julia> tonne(MTS) # t
1.0

julia> tonne(English) # lb
2204.622621848776

julia> tonne(British) # slug
68.52176585679176

julia> tonne(Gravitational) # hyl
101.97162129779284
```
