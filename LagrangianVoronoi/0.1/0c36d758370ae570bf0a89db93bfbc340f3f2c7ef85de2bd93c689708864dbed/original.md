```
stiffened_eos!(grid::VoronoiGrid, gamma = 1.4; P0)
```

Compute pressure and sound speed from internal energy and density using ideal gas equation of state. Number `gamma` is adiabatic index and `P0` is the stiffness constant. Stiffened equation of state fares better for flows with very low Mach number.
