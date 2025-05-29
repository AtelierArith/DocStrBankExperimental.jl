```
read_edges!(sim::Simulation, [name::String = sim.filename; idmapfunc = identity, transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
read_edges!(sim::Simulation, nr::Int64; [ idmapfunc = identity, transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
```

Read the edges from an HDF5 file into the simulation `sim`. If `name` is given, the edges are read from the file with this filename from the `h5` subfolder of the current working directory.  In the other case the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

Per default, the edge states from the last transition function written to the file are read. The `transition` keyword allows to read also earlier versions. Alternatively, the comment that was specified when write_snapshot was called can be specified with the `comment` keyword to read the corresponding snapshot.

If only the edges of a subset of edge types are to be read, this subset can be specified via the optional `types` argument.

When the edges from a distributed simulation is read into a single threaded simulation, the IDs of the agents are modified.  The `idmapfunc` must be a function that must return the new agent id for a given old agent id. [`read_agents!`](@ref) returns a `Dict{AgentID, AgentID}` that can be used for this via: `idmapfunc = (key) -> idmapping[key]`, where `idmapping` is such a `Dict`.
