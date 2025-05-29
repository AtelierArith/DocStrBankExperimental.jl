```
read_var(paths::Vector{String}; short_name = nothing)
```

Read the `short_name` variable in the vector of NetCDF files.

This function automatically aggregates the NetCDF files along the time dimension. If this is not possible, then an error is thrown. The attributes of the OutputVar is the same as the attributes of the first NetCDF file.

When `short_name` is `nothing`, automatically identify the name of the variable. If multiple variables are present, the last one in alphabetical order is chosen.

When `units` is among the attributes, try to parse it and convert it into an [`Unitful`](https://painterqubits.github.io/Unitful.jl) object. `OutputVar`s with `Unitful` support automatic unit conversions.

If you want to access `units` as a string, look at [`units`](@ref) function.

# Example

```julia
simdir = SimDir("my_output")
read_var(simdir.variable_paths["hu"]["inst"])

read_var(["my_netcdf_file1.nc", "my_netcdf_file2.nc"], short_name = "ts")
```
