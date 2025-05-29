```
StoreTrajectories{F<:Format} <: AriannaAlgorithm
```

Algorithm to store system trajectories during simulation.

# Fields

  * `paths::Vector{String}`: Paths to output files
  * `files::Vector{IOStream}`: File handles for writing trajectories
  * `fmt::F`: Format type for output files
  * `store_first::Bool`: Whether to store trajectories at initialization
  * `store_last::Bool`: Whether to store trajectories at finalization
