```Julia
slinch(U::UnitSystem) = mass(𝟏,U,IPS)
```

British gravitational `slinch` unit of `mass` (kg or lb).

```Julia
julia> slinch(Metric) # kg
175.12683524647633

julia> slinch(CGS) # g
175126.83524647634

julia> slinch(English) # lb
386.0885826771652

julia> slinch(British) # slug
11.999999999999998

julia> slinch(Gravitational) # hyl
17.857967322834643
```
