```
read_sim_metadata(sim::Simulation, [ key::Symbol = Symbol() ])
read_sim_metadata(filename::String, [ key::Symbol = Symbol() ])
```

Read metadata for a simulation or from the file `filename`. Metadata is stored via `key`, value pairs. If `key` is not set (or set to Symbol()), a Dict{Symbol, Any} with the complete metadata of the simulation is returned.

The following metadata is stored automatically:

  * simulation_name
  * model_name
  * date (in the format "yyyy-mm-dd hh:mm:ss")

See also: [`write_metadata`](@ref)
