```Julia
lorentz(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/rationalization(U)
```

ローレンツの法則の力に対する電磁比例定数 `αL`（無次元）。

```Julia
julia> lorentz(Metric)
1

julia> lorentz(LorentzHeaviside)
3.335640951981521e-11

julia> lorentz(Gauss)
3.335640951981521e-11
```
