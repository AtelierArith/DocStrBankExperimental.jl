```
to_netcdf(data, dest::AbstractString; group::Symbol=:posterior, kwargs...)
to_netcdf(data, dest::NCDatasets.NCDataset; group::Symbol=:posterior)
```

Write `data` to a NetCDF file.

`data` is any type that can be converted to an [`InferenceData`](@ref) using [`convert_to_inference_data`](@ref). If not an `InferenceData`, then `group` specifies which group the data represents.

`dest` specifies either the path to the NetCDF file or an opened NetCDF file. If `dest` is a path, remaining `kwargs` are passed to [`NCDatasets.NCDataset`](@extref).

!!! note
    This method requires that NCDatasets is loaded before it can be used.


# Examples

```julia
julia> using InferenceObjects, NCDatasets

julia> idata = from_namedtuple((; x = randn(4, 100, 3), z = randn(4, 100)))
InferenceData with groups:
  > posterior

julia> to_netcdf(idata, "data.nc")
"data.nc"
```
