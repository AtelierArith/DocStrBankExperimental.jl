```Julia
eotvos(U::UnitSystem) = specificforce(nano,U,Gauss)/length(𝟏,U,Gauss)
```

Metric unit of `specificforce` per `length` used in gravimetry (s⁻² or gal⋅cm⁻¹).

```Julia
julia> eotvos(Metric) # s⁻²
9.999999999999999e-10

julia> eotvos(CGS) # gal⋅cm⁻¹
1.0e-9

julia> eotvos(English) # lbf⋅lbm⁻¹ft⁻¹
3.108095017156726e-11
```
