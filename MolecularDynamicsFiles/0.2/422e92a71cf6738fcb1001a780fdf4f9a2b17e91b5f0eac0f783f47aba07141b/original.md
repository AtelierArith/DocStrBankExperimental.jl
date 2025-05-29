```julia
mutable struct ReadTrajectory
```

Represents a molecular dynamics trajectory stored on disk.

A trajectory consists of a set of states of a molecular simulation.   This structure allows for iteration over the states that are contained in trajectory files on disk.

# Fields:

  * `format`: the file format of the trajectory files
  * `filepaths`: paths to files of the trajectory files containing snapshots
  * `fmasktimesteps`: timesteps inferred from filenames (integers read from file mask)
  * `i`: index of file currently being read
  * `io`: input filestream of currently read file
