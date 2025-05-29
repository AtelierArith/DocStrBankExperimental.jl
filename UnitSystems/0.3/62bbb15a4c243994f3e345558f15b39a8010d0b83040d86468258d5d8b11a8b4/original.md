```Julia
lunarmass(U::UnitSystem) = earthmass(U)/μE☾
```

Lunar `mass` estimated from `μE☾` Earth-Moon mass ratio (kg or slug).

```Julia
julia> lunarmass(Metric) # kg
7.345787071534757e22

julia> lunarmass(British) # slug
5.033463017495526e21

julia> lunarmass(English) # lb
1.6194688353189796e23

julia> lunarmass(IAU) # M☉
3.69430341216115e-8

julia> lunarmass(IAUE) # ME
0.012300037067391707

julia> lunarmass(IAUJ) # MJ
3.870024740923696e-5

julia> lunarmass(QCD) # mₚ
4.3917797366372566e49

julia> lunarmass(Metric)/dalton(Metric) # Da
4.4237363752976815e49
```
