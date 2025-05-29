```
mutable struct Simulation{S, A, VS}
```

A structure representing a Monte Carlo simulation.

# Fields

  * `chains::Vector{S}`: Vector of independent Arianna systems.
  * `algorithms::A`: List of algorithms.
  * `steps::Int`: Number of MC sweeps.
  * `t::Int`: Current time step.
  * `schedulers::VS`: List of schedulers (one for each algorithm).
  * `counters::Vector{Int}`: Counters for the schedulers (one for each algorithm).
  * `path::String`: Simulation path.
  * `verbose::Bool`: Flag for verbose output.
