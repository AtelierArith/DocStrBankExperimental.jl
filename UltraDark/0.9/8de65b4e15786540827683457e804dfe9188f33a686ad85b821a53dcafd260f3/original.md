```
simulate!(grids, output_config::OutputConfig; constants = nothing, external_states = (),)
simulate!(grids, sim_config, output_config::OutputConfig; constants = nothing, external_states = (),)
```

`simulate!` is the main entry point into a simulation

`simulate!` evolves `grids` and `external_states` forward, writing output as specified by `output_config`.

# Arguments

`grids::AbstractGrids` Contains coordinate systems and the scalar field `ψ`.

`sim_config::UltraDark.Config` gives further control over the way the simulation is done.

`output_config::OutputConfig` controls what output is written and when.

`constants::Any` can be used to overload other functions in the evolution, for example to introduce self-interactions.

`external_states::Tuple{Any}` can be used in combination with overloading to add other dynamical objects to a simulation.
