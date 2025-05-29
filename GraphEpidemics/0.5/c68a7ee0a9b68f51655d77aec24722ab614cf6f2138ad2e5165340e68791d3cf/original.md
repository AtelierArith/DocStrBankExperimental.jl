`run_complex_contagion(model::AbstractEpiModel, g::AbstractGraph, T::Integer, rng::AbstractRNG, data::SimData; spreading_function::Function = is_spreading, verbose::Bool = false)`

Simulates the spread of contagion across a network over a fixed number of time steps.

Applies independent and spreading transitions from time `0` to `T`, updating the simulation state in-place. Returns a vector of NamedTuples tracking the number of nodes in each state at each timestep.

### Optional Arguments

  * `spreading_function`: A custom function to determine if infection spreads between neighbors.
  * `verbose`: If true, prints additional debug information.
