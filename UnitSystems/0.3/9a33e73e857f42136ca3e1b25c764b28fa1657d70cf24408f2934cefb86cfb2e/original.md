```Julia
ton(U::UnitSystem) = mass(𝟐*kilo,U,English)
```

English `ton` unit of `mass` (kg or lb).

```Julia
julia> ton(Metric) # kg
907.18474

julia> ton(MTS) # t
0.9071847400000002

julia> ton(English) # lb
2000

julia> ton(British) # slug
62.16190034313451

julia> ton(Gravitational) # hyl
92.50709875441666
```
