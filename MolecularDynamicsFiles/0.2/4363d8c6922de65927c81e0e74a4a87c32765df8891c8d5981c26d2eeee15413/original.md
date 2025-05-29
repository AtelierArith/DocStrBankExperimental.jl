```julia
struct MDFrame
```

Represents a snapshot of the molecular simulation.

Particles are stored in a table (DataFrame) with rows representing particles and columns representing particle properties.  

Column names are in LAMMPS notation (see [dump command documentation](https://docs.lammps.org/dump.html)).

The particle table is sorted by the column with name `:id`, if it exists.  

Commonly used particle properties can be accessed by specific MDFrame methods. The properties are (in LAMMPS notation): `:id`, `:mol`, `:type`, `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz`, `:vx`, `:vy`, `:vz`, `:element`, `:mass`. Any other properties are considered 'extra' and are accessed by using the method [`extra_scalars`](@ref).

Some of the methods for accessing particle properties generate the data if it's not present in the frame, for example: particle types may be generated from particle elements or masses.

# Fields:

  * `timestep`: Timestep of the snapshot
  * `box`: Simulation box specification
  * `particles`: Table containing particle data.
  * `system_properties`: Dict containing other arbitrary system properties, like 'units' and 'time' of LAMMPS Dump or 'A' and 'R' of CFG.
