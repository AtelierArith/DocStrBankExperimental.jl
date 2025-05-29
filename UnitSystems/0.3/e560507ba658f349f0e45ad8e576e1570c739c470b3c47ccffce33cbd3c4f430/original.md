```Julia
galileo(U::UnitSystem) = specificforce(𝟏,U,Gauss)
```

Metric unit of `specificforce` used in gravimetry (m⋅s⁻² or ft⋅s⁻²).

```Julia
julia> galileo(Metric) # m⋅s⁻²
0.01

julia> galileo(CGS) # gal
1

julia> galileo(English) # lbf⋅lbm⁻¹
0.0010197162129779284
```
