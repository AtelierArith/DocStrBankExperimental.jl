```Julia
molarmass(U::UnitSystem) = avogadro(U)*electronmass(U)/electronunit(U)
```

Molar mass constant `Mᵤ` is the ratio of the `molarmass` and `relativemass` of a chemical.

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
