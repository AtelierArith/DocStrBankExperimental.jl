```Julia
bohr(U::UnitSystem) = planckreduced(U)*gravity(U)/electronmass(U)/lightspeed(U)/finestructure(U)
```

水素原子の基底状態におけるボーア半径 `a₀` (m)。

```Julia
julia> bohr(Metric) # m
5.291772109022829e-11

julia> bohr(IPS) # in
2.0833748460719797e-9

julia> bohr(Hartree) # a₀
1.0
```
