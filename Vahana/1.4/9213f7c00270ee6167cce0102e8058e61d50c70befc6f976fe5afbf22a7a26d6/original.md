```
create_h5file!(sim::Simulation, [filename = sim.filename; overwrite = sim.overwrite_file])
```

The canonical way to create an HDF5 file is to call one of the `write_` functions like [`write_snapshot`](@ref). If `sim` does not already have an HDF5 file attached, such a file will then be created automatically using the filename specified as keyword in [`create_simulation`](@ref) or, if this keyword was not given, the model name. But sometime it can be useful to control this manually, e.g. after a call to [`copy_simulation`](@ref).

The `filename` argument can be used to specify a filename other than `sim.filename`. If `overwrite` is true, existing files with this name will be overwritten. If it is false, the filename is automatically extended by an increasing 6-digit number, so that existing files are not overwritten.

By default, the files are created in an `h5` subfolder, and this is created in the current working directory. However, the path can also be set with the function `set_hdf5_path`.

In the case that an HDF5 file was already created for the simulation `sim`, this will be closed.

`create_h5file!` can be only called after [`finish_init!`](@ref)

See also [`close_h5file!`](@ref), [`write_agents`](@ref), [`write_edges`](@ref), [`write_globals`](@ref), [`read_agents!`](@ref), [`read_edges!`](@ref), [`read_globals`](@ref), [`read_snapshot!`](@ref) and [`list_snapshots`](@ref)
