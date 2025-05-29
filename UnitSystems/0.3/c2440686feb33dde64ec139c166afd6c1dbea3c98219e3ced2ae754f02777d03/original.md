```Julia
rationalization(U::UnitSystem) = spat(U)*biotsavart(U)/vacuumpermeability(U)/lorentz(U)
```

Constant of magnetization and polarization density or `spat(U)*coulomb(U)*permittivity(U)`.

```Julia
julia> rationalization(Metric)
1

julia> rationalization(Gauss)
12.566370614359172
```
