```
ideal_eos!(grid::VoronoiGrid, gamma = 1.4; Pmin)
```

Compute pressure and sound speed from internal energy and density using ideal gas equation of state. Number `gamma` is adiabatic index and `Pmin` can specify least possible value pressure. In the semi-implicit scheme, this value of pressure is used as an initial condition for an implicit solver.
