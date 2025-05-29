```
hdf2imas(filename::AbstractString, target_path::AbstractString; error_on_missing_coordinates::Bool=true, verbose::Bool=false, kw...)
```

Load an object from an HDF5 file using a simple entry point. Given a file and an internal target path (as a string), the function returns either the dataset’s value or an IMAS ids structure constructed from a group.

If the object at `target_path` is a group and has a "concrete*type" attribute, that type is evaluated and instantiated; otherwise, a default (`dd()`) is used. Coordinate data is processed based on `error*on*missing*coordinates`.

# Arguments

  * `filename`: Path to the HDF5 file
  * `target_path`: Internal HDF5 path to the desired dataset or group
  * `error_on_missing_coordinates` (default: `true`): Enforce coordinate checks
  * `verbose` (default: `false`): Enable verbose logging
  * `kw...`: Additional keyword arguments passed to `HDF5.h5open`

# Returns

The value of the dataset or the constructed IMAS ids.
