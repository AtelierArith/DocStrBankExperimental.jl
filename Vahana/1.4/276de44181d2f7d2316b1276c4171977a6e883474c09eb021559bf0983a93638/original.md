```
close_h5file!(sim::Simulation)
```

Closes the HDF5 file attached to the simulation `sim`.

Be aware that a following call to one of the `write_` functions like [`write_snapshot`](@ref) will automatically create a new file and, depending on the `overwrite_file` argument of [`create_simulation`](@ref) also overwrites to closed file.
