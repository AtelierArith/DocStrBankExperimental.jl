```
read_globals(filename::String, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(sim::Simulation, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(sim::Simulation, nr::Int64, T::DataType; [ transition = typemax(Int64), comment = "" ])
read_globals(filename::String; [ transition = typemax(Int64), comment = "" ])
```

Read the global values from an HDF5 file. If `filename` is given, the parameters are read from the file with this filename from the `h5` subfolder of the current working directory.

If a simulation `sim` is given instead, the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

In the case that the DataType `T` of the argument `globals` of [`create_simulation`](@ref) used for the simulation is specified, the result will be an instance of T, elsewhere it will be a Dict with the fields of the written Globals type as keys.

Per default, the last written globals are read. The `transition` keyword allows to read also earlier versions. Alternatively, the comment that was specified when write_snapshot was called can be specified with the `comment` keyword to read the corresponding snapshot.

See also [File storage](./hdf5.md) for details.
