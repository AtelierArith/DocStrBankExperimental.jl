```
read_snapshot!(sim::Simulation, [name::String; transition = typemax(Int64), comment = "", writeable = false, ignore_params = false])
read_snapshot!(sim::Simulation, nr::Int64; [transition = typemax(Int64), comment = "", writeable = false, ignore_params = false])
```

Read a complete snapshot from a file into the simulation `sim`. If `name` is given, the snapshot is read from the file with this filename from the `h5` subfolder of the current working directory.  In the other case the filename from the [`create_simulation`](@ref) call is used.

If the `overwrite_file` argument of [`create_simulation`](@ref) is set to true, and the file names are supplemented with a number, the number of the meant file can be specified via the `nr` argument.

Per default, the last written snapshot is read. The `transition` keyword allows to read also earlier versions. Alternatively, the comment that was specified when write_snapshot was called can be specified with the `comment` keyword to read the corresponding snapshot.

If `writeable` is set to true, the file is also attached to the simulation and following `write_` functions like [`write_snapshot`](@ref) will be append to the file.

If `ignore_params` is set to true, the parameters of `sim` will not be changed.

Returns false when no snapshot was found 
