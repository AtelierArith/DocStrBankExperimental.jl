```
read_combined_h5(filename::AbstractString; show_warnings::Bool=true, error_on_missing_coordinates::Bool=true, pattern::Regex=r"", kw...)
```

Iteratively traverse an HDF5 file from the root ("/") using a stack.

# Arguments

  * `filename`: Path to the combined HDF5 file
  * `error_on_missing_coordinates` (default `true`): Enforce coordinate checks during dispatch
  * `pattern` (default `r""`): A regex used to filter which paths are processed
  * `kw...`: Additional keyword arguments passed to `hdf2imas`

# Returns

  * `Dict{String,Any}`: loaded data with keys (path as string)
