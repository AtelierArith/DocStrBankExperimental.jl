```Julia
solarmass(U::UnitSystem) = mass(1.9884092485076926e30,U)
```

Solar `mass` estimated from gravitational constant estimates (kg or slug).

```Julia
julia> solarmass(Metric) # kg
1.9884092485076926e30

julia> solarmass(British) # slug
1.3624931295372337e29

julia> solarmass(English) # lb
4.383692010753383e30

julia> solarmass(IAUE) # ME
332946.04408781475

julia> solarmass(IAUJ) # MJ
1047.5654837077257

julia> solarmass(QCD) # mₚ
1.1887977912642768e57

julia> solarmass(Metric)/dalton(Metric) # Da
1.1974480387115297e57
```
