```Julia
pound(U::UnitSystem) = mass(𝟏,U,English)
```

English `pound` unit of `mass` (kg or lb).

```Julia
julia> pound(Metric) # kg
0.45359237

julia> pound(CGS) # g
453.5923700000001

julia> pound(English) # lb
1

julia> pound(British) # slug
0.031080950171567256

julia> pound(Gravitational) # hyl
0.04625354937720833
```
