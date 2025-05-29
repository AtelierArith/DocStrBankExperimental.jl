```Julia
molarmass(U::UnitSystem) = avogadro(U)*electronmass(U)/electronunit(U)
```

モル質量定数 `Mᵤ` は、化学物質の `molarmass` と `relativemass` の比率です。

```Julia
julia> molarmass(CGS) # g⋅mol⁻¹
1

julia> molarmass(Metric) # kg⋅mol⁻¹
0.001

julia> molarmass(SI2019) # kg⋅mol⁻¹
0.000999999999656256

julia> molarmass(International) # kg⋅mol⁻¹
0.000999835000017957
```
