```Julia
liter(U::UnitSystem) = volume(𝟏𝟎^-3,U,Metric)
```

Unit of `volume` derived from 1 cubic decimeter (m³ or ft³).

```Julia
julia> liter(Metric) # m³
0.001

julia> liter(CGS) # cm³
999.9999999999994

julia> liter(IPS) # in³
61.02374409473224
```
