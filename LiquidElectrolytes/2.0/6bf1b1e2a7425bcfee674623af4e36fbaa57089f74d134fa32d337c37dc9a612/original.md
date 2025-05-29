```
PBSystem(grid;
             celldata=ElectrolyteData(),
         bcondition=(f, u, n, e)-> nothing,
         kwargs...)
```

Create VoronoiFVM system generalized Poisson-Boltzmann. Input:

  * `grid`: discretization grid
  * `celldata`: composite struct containing electrolyte data
  * `bcondition`: boundary condition
  * `kwargs`: Keyword arguments of VoronoiFVM.System
