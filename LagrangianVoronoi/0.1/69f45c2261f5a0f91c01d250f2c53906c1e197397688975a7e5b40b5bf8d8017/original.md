```
SimulationWorkspace
```

Abstract type for containing the computational grid, solvers and global variables. This methods should be defined for an instance `sim` of SimulationWorkspace:

  * step!(sim, time::Float64)
  * postproc!(sim, time::Float64) [optional]
