```
read_params(filename::String, T::DataType)
read_params(sim::Simulation, T::DataType)
read_params(sim::Simulation, nr::Int64, T::DataType)
read_params(filename::String)
```

Read the parameters from an HDF5 file. If `filename` is given, the parameters are read from the file with this filename from the `h5` subfolder of the current working directory.

If a simulation `sim` is given instead, the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

In the case that the DataType `T` of the argument `globals` of [`create_simulation`](@ref) used for the simulation is specified, the result will be an instance of T, elsewhere it will be a Dict with the fields of the written Globals type as keys.
