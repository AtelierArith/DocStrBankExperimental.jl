```julia
nc_write(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{NetCDFTools.NcDim};
    ...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}
nc_write(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{NetCDFTools.NcDim},
    attrib::Dict;
    overwrite,
    mode,
    kw...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}

```

# Arguments

  * `mode`: one of "r", "c", "w", see [NCDatasets.nc_open()] for details

      * "a": append
      * "c": create
  * `units`: units of the variable
  * `longname`: longname of the variable
  * attrib: An iterable of attribute name and attribute value pairs, for example a Dict, DataStructures.OrderedDict or simply a vector of pairs (see example below)
  * `type`: which type to save? Julia variable types.
  * `kwargs`: Parameters passed to `ncvar_def`, and further to [`NCDatasets.defVar`]. For examples:

      * fillvalue: A value filled in the NetCDF file to indicate missing data. It will be stored in the _FillValue attribute.
      * chunksizes: Vector integers setting the chunk size. The total size of a chunk must be less than 4 GiB. Such as `(10, 10, 1)`
      * shuffle: If true, the shuffle filter is activated which can improve the compression ratio.
      * checksum: The checksum method can be :fletcher32 or :nochecksum (checksumming is disabled, which is the default)

# Examples

```julia
dims = [
    NcDim("lon", lon, Dict("longname" => "Longitude", "units" => "degrees east"))
    NcDim("lat", lat, Dict("longname" => "Latitude", "units" => "degrees north"))
    NcDim_time(dates)
]

b = bbox(70, 15, 140, 55)
cellsize=1
dates = Date(2010):Day(1):Date(2010, 1, 4) |> collect
dims = NcDims(b, cellsize, dates) # one option

nc_write(f, varname, val, dims; units, longname)
```

```julia
nc_write(f, varname, val, dims; ...)
nc_write(
    f,
    varname,
    val,
    dims,
    attrib;
    overwrite,
    mode,
    kw...
)
```

defined at [`packages/NetCDFTools/QX4TD/src/nc_write.jl:55`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/nc_write.jl).

@seealso `ncvar_def`
