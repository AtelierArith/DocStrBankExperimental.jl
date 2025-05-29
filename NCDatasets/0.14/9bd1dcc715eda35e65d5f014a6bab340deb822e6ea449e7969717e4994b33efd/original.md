```
NCDataset(filename::AbstractString, mode = "r";
          format::Symbol = :netcdf4,
          share::Bool = false,
          diskless::Bool = false,
          persist::Bool = false,
          memory::Union{Vector{UInt8},Nothing} = nothing,
          attrib = [])
```

Load, create, or even overwrite a NetCDF file at `filename`, depending on `mode`

  * `"r"` (default) : open an existing netCDF file or OPeNDAP URL  in read-only mode.
  * `"c"` : create a new NetCDF file at `filename` (an existing file with the same name will be overwritten).
  * `"a"` : open `filename` into append mode (i.e. existing data in the netCDF file is not overwritten and a variable can be added).

If `share` is true, the `NC_SHARE` flag is set allowing to have multiple processes to read the file and one writer process (netcdf classic files only). Likewise setting `diskless` or `persist` to `true` will enable the flags `NC_DISKLESS` or `NC_PERSIST` flag. More information is available in the [NetCDF C-API](https://www.unidata.ucar.edu/software/netcdf/docs/).

Notice that this does not close the dataset, use `close` on the result (or see below the `do`-block).

The optional parameter `attrib` is an iterable of attribute name and attribute value pairs, for example a `Dict`, `DataStructures.OrderedDict` or simply a vector of pairs (see example below).

# Supported `format` values:

  * `:netcdf4` (default): HDF5-based NetCDF format.
  * `:netcdf4_classic`: Only netCDF 3 compatible API features will be used.
  * `:netcdf3_classic`: classic netCDF format supporting only files smaller than 2GB.
  * `:netcdf3_64bit_offset`: improved netCDF format supporting files larger than 2GB.
  * `:netcdf5_64bit_data`: improved netCDF format supporting 64-bit integer data types.

Files can also be open and automatically closed with a `do` block.

```julia
NCDataset("file.nc") do ds
    data = ds["temperature"][:,:]
end
```

Here is an attribute example:

```julia
using DataStructures
NCDataset("file.nc", "c", attrib = OrderedDict("title" => "my first netCDF file")) do ds
   defVar(ds,"temp",[10.,20.,30.],("time",))
end;
```

The NetCDF dataset can also be a `memory` as a vector of bytes. A non-empty string a `filename` is still required, for example:

```julia
using NCDataset, HTTP
resp = HTTP.get("https://www.unidata.ucar.edu/software/netcdf/examples/ECMWF_ERA-40_subset.nc")
ds = NCDataset("some_string","r",memory = resp.body)
total_precipitation = ds["tp"][:,:,:]
close(ds)
```

`Dataset` is an alias of `NCDataset`.
