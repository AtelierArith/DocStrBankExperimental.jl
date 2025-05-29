```
heat_from_bdary!(grid::VoronoiGrid, dt::Float64, T_bc::Function)
```

Update the internal energy of a Voronoi cell by considering heat flux from boundary. Function `T_bc` specifies the temperature at that boundary and should return `NaN`  to indicate adiabatic walls. This currently works only for ideal gas.
