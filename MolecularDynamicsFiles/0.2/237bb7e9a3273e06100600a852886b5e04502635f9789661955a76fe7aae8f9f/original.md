```julia
struct SimulationBox
```

Stores the properties of the simulation box of a particle system.

# Fields:

  * `basis`: simulation box vectors stored in columns
  * `origin`: simulation box origin
  * `bc`: boundary conditions
  * `istriclinic`: box is triclinic flag
