```
Output
```

Abstract supertype for simulation outputs.

Outputs are store or display simulation results, usually as a vector of grids, one for each timestep - but they may also sum, combine or otherwise manipulate the simulation grids to improve performance, reduce memory overheads or similar.

Simulation outputs are decoupled from simulation behaviour, and in many cases can be used interchangeably.
