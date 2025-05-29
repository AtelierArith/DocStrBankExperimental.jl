```
finish_simulation!(sim)
```

This function removes all agents/edges and rasters from the simulation to minimize the memory footprint, closes all open files and finalizes MPI. The `parameters` and `globals` of the simulation are still available, the remaining state of the simulation is undefined.

!!! warning
    In a REPL session the function serves as a finalizer for the simulation object ('sim'). But for parallel simulation it is essential that this function is called manually before the termination of the simulation.


Returns the `globals` of the simulation.
