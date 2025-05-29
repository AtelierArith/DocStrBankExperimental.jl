```
PNPSystem(grid;
         celldata=ElectrolyteData(),
         bcondition=(f, u, n, e)-> nothing,
         reaction=(f, u, n, e)-> nothing,
         kwargs...)
```

Create VoronoiFVM system for generalized Poisson-Nernst-Planck. Input:

  * `grid`: discretization grid
  * `celldata`: composite struct containing electrolyte data
  * `bcondition`: boundary condition
  * `reaction` : reactions of the bulk species
  * `kwargs`: Keyword arguments of VoronoiFVM.System
