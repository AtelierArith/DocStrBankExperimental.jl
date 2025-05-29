```Julia
lorentz(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/rationalization(U)
```

Electromagnetic proportionality constant `αL` for the Lorentz's law force (dimensionless).

```Julia
julia> lorentz(Metric)
1

julia> lorentz(LorentzHeaviside)
3.335640951981521e-11

julia> lorentz(Gauss)
3.335640951981521e-11
```
