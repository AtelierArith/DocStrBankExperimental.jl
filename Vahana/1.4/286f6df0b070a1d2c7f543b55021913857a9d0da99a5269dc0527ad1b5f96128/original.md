```
list_snapshots(name::String)
list_snapshots(sim::Simulation)
list_snapshots(sim::Simulation, nr::Int64)
```

List all snapshots of a HDF5 file. If `name` is given, the snapshots from the file with this filename is returned.  In the other case the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

Returns a vector of tuples, where the first element is the transition number for which a snapshot was saved, and the second element is the comment given in the [`write_snapshot`](@ref) call.
