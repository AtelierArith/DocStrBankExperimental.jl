```Julia
electronvolt(U::UnitSystem) = elementarycharge(U)*volt(U)
```

Unit of `energy` gained by a rest electron accelerated by 1 `volt` in vacuum (J or lb⋅ft).

```Julia
julia> electronvolt(SI2019) # J
1.602176634e-19

julia> electronvolt(SI2019)/lightspeed(SI2019) # kg⋅m⋅s⁻¹
5.344285992678308e-28

julia> electronvolt(SI2019)/lightspeed(SI2019)^2 # kg
1.7826619216278975e-36

julia> electronvolt(SI2019)/planck(SI2019)/lightspeed(SI2019) # m⁻¹
806554.3937349211

julia> electronvolt(SI2019)/boltzmann(SI2019) # K
11604.518121550082
```
