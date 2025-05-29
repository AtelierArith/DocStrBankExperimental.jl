```Julia
slug(U::UnitSystem) = mass(𝟏,U,British)
```

British gravitational `slug` unit of `mass` (kg or lb).

```Julia
julia> slug(Metric) # kg
14.593902937206364

julia> slug(CGS) # g
14593.902937206363

julia> slug(English) # lb
32.17404855643044

julia> slug(British) # slug
1

julia> slug(Gravitational) # hyl
1.4881639435695537
```
