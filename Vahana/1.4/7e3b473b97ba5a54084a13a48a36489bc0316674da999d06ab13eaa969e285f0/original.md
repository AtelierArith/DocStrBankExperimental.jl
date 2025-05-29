```
read_edges(filename::String, type; transition = typemax(Int64), comment = "")
```

Read the edgestates of `type` (which can be a DataType, String or Symbol) from an HDF5 file with the name `filename`.  The edgestates are read from the `h5` subfolder of the current working directory, or from the subfolder set with [`set_hdf5_path`](@ref).

Per default, the edge states from the last transition function written to the file are read. The `transition` keyword allows to read also earlier versions. Alternatively, the comment that was specified when write_snapshot was called can be specified with the `comment` keyword to read the corresponding snapshot.

Returns a vector of edges. In parallel simulations, the vector includes only edges where the write operation originated from the same rank as the current process. When the current session runs with a single process (size = 1), the edges from all ranks are consolidated into the returned vector.
