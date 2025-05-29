```Julia
rationalization(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/lorentz(U)
```

磁化定数と偏極密度の定数または `spat(U)*coulomb(U)*permittivity(U)`。

```Julia
julia> rationalization(Metric)
1

julia> rationalization(Gauss)
12.566370614359172
```
