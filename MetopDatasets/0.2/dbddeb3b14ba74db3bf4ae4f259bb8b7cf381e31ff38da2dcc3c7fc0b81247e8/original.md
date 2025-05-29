```
MetopDataset(file_path::AbstractString; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
MetopDataset(file_pointer::IO; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
MetopDataset(f::Function, file_path::AbstractString; auto_convert::Bool = true, high_precision::Bool=false, maskingvalue = missing)
```

Load a MetopDataset from a Metop Native binary file or from a `IO` to a Native binary file. Only the meta data is loaded upon creation and all variables are lazy loaded.  The variables corresponds to the different fields of the data records in the file. The attributes have all the information from the main product header in the file.

`auto_convert=true` will automatically convert `MetopDatasets` specific types such as `VInteger` to common netCDF complaint types such as `Float64`. This will also automatically scale variable where the  scaling can't be expressed through a simple scale factor e.g. the IASI spectrum where different bands of  the spectrum have different scaling factors.

Selected fields are converted to `Float32` to save memory. Normally `Float32` is more than sufficient to represent the instrument accuracy.  Setting `high_precision=true` will in some case convert these variables to `Float64`. 

`maskingvalue = NaN` will replace `missing` values with NaN. This normally floats but can create issues for integers. See documentation page for more information.

## Example

```julia-repl
julia> file_path = "test/testData/ASCA_SZR_1B_M03_20230329063300Z_20230329063558Z_N_C_20230329081417Z"
julia> ds = MetopDataset(file_path);
julia>
julia> # display metadata of a variable
julia> ds["latitude"]
latitude (82 × 96)
  Datatype:    Union{Missing, Float64} (Int32)
  Dimensions:  xtrack × atrack
  Attributes:
   description          = Latitude (-90 to 90 deg)
   missing_value        = Int32[-2147483648]
   scale_factor         = 1.0e-6
julia>
julia> # load a subset of a variable  
julia> lat_subset = ds["latitude"][1:2,1:3] # load a small subset of latitudes.
2×3 Matrix{Union{Missing,Float64}}:
    -33.7308  -33.8399  -33.949
    -33.7139  -33.823   -33.9322
julia>
julia> # load entire variable  
julia> lat = ds["latitude"][:,:]
julia>
julia> # close data set
julia> close(ds);
```
