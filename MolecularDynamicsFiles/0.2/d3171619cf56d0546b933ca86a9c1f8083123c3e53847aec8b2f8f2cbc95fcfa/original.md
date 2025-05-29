```julia
mutable struct WriteTrajectory
```

Represents a molecular dynamics trajectory being written to disk.

A trajectory consists of a set of states of a molecular simulation. This structure allows for writing frames into a trajectory sequentially.

# Fields

  * `format`: trajectory file format
  * `exported_particle_properties`: particle properties written into trajectory
  * `filepath`: path to trajectory (filename may contain mask '*')
  * `io`: current output file stream
  * `isopen`: trajectory is open flag
