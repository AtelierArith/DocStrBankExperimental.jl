```Julia
jupitermass(U::UnitSystem) = mass(1.8981240594811976e27,U)
```

Jupiter `mass` estimated from gravitational constant estimates (kg or slug).

```Julia
julia> jupitermass(Metric) # kg
1.8981240594811976e27

julia> jupitermass(British) # slug
1.3006281237091369e26

julia> jupitermass(English) # lb
4.1846472406076795e27

julia> jupitermass(IAU) # M☉
0.0009545942621750254

julia> jupitermass(IAUE) # ME
317.828383300101

julia> jupitermass(QCD) # mₚ
1.1348195504272223e54

julia> jupitermass(Metric)/dalton(Metric) # Da
1.1430770270067641e54
```
