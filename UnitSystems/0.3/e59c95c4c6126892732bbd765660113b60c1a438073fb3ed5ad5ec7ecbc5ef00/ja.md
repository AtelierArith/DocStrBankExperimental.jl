```Julia
klitzing(U::UnitSystem) = planck(U)/elementarycharge(U)^2
```

量子ホール抵抗 `RK` (Ω)。

```Julia
julia> klitzing(SI2019) # Ω
25812.807459304513

julia> klitzing(Metric) # Ω
25812.80744523112

julia> klitzing(Conventional) # Ω
25812.807

julia> klitzing(International) # Ω
25800.036427199655

julia> klitzing(CODATA) # Ω
25812.8074555

julia> klitzing(EMU) # abΩ
2.5812807445231113e13

julia> klitzing(ESU) # statΩ
2.8720621650837648e-8
```
