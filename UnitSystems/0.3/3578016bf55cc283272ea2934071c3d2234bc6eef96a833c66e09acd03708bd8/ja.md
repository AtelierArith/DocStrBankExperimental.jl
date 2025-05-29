```Julia
earthmass(U::UnitSystem) = mass(5.972166613228324e24,U)
```

地球の `mass` は重力定数の推定値から算出されています (kg または slug)。

```Julia
julia> earthmass(Metric) # kg
5.972166613228324e24

julia> earthmass(British) # slug
4.092234023293802e23

julia> earthmass(English) # lb
1.316637361697315e25

julia> earthmass(IAU) # M☉
3.003489657730396e-6

julia> earthmass(IAUJ) # MJ
0.0031463520961114936

julia> earthmass(QCD) # mₚ
3.5705418711949936e51

julia> earthmass(Metric)/dalton(Metric) # Da
3.596522799939627e51
```
