```
MultiphaseSolver(grid::VoronoiGrid, quality_threshold::Float64 = 0.25)
```

Construct a solver for the multiphase projection step.  A keyword argument `quality_threshold` determines when `dv` should not be projected because the quality of the cell is too poor. In these problematic cases, stability of the simulation takes priority over physical accuracy. 
