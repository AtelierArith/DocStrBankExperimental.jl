```Julia
electronradius(U::UnitSystem) = finestructure(U)*planckreduced(U)*gravity(U)/electronmass(U)/lightspeed(U)
```

古典電子半径またはローレンツ半径またはトムソン散乱長 (m)。

```Julia
julia> electronradius(Metric) # m
2.8179403261891358e-15

julia> electronradius(CODATA) # m
2.8179403261891366e-15

julia> electronradius(Conventional) # m
2.817940326189136e-15

julia> electronradius(Hartree) # a₀
5.3251354520432896e-5
```
