```Julia
gram(U::UnitSystem) = mass(𝟏,U,Gauss)
```

Metric `gram` unit of `mass` (kg or lb).

```Julia
julia> gram(Metric) # kg
0.001

julia> gram(CGS) # g
1

julia> gram(English) # lb
0.002204622621848776

julia> gram(British) # slug
6.852176585679177e-5

julia> gram(Gravitational) # hyl
0.00010197162129779283
```
