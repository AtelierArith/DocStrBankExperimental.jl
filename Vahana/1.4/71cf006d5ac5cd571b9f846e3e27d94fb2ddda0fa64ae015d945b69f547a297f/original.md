```
read_agents!(sim::Simulation, [name::String = sim.filename; transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
read_agents!(sim::Simulation, nr::Int64; [transition = typemax(Int64), types::Vector{DataType}, comment = "" ])
```

Read the agents from an HDF5 file into the simulation `sim`. If `name` is given, the agent are read from the file with this filename from the `h5` subfolder of the current working directory, or from the subfolder set with [`set_hdf5_path`](@ref). In the other case the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

Per default, the agent states from the last transition function written to the file are read. The `transition` keyword allows to read also earlier versions. Alternatively, the comment that was specified when write_snapshot was called can be specified with the `comment` keyword to read the corresponding snapshot.

If only the agents of a subset of agent types are to be read, this subset can be specified via the optional `types` argument.

When the agents from a distributed simulation is read into a single threaded simulation, the IDs of the agents are modified.  `read_agents!` returns a dictory that contains the ID mapping.
