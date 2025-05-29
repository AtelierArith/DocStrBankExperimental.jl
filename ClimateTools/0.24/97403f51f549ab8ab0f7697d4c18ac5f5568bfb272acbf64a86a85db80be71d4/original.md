```
load(file::String, vari::String; poly = Array{Float64}([]), start_date::Tuple, end_date::Tuple, data_units::String = "")
```

Returns a ClimGrid type with the data in **file** of variable **vari** inside the polygon **poly**. Metadata is built-in the ClimGrid type, from the netCDF attributes.

Inside the ClimgGrid type, the data is stored into an AxisArray data type, with time, longitude/x and latitude/y dimensions.

The polygon provided should be in the -180, +180 longitude format. If the polygon crosses the International Date Line, the polygon should be splitted in multiple parts (i.e. multi-polygons).

Options for data_units are for precipitation : "mm", which converts the usual "kg m-2 s-1" unit found in netCDF files. For temperature : "Celsius", which converts the usual "Kelvin" unit.

Temporal subsetting can be done by providing start_date and end-date Tuples of length 1 (year), length 3 (year, month, day) or 6 (hour, minute, second).

**Note:** load uses [CF conventions](http://cfconventions.org/). If you are unable to read the netCDF file with load, the user will need to read it with low-level functions available in [NetCDF.jl package](https://github.com/JuliaGeo/NetCDF.jl) or [NCDatasets.jl](https://github.com/Alexander-Barth/NCDatasets.jl) or re-create standartized netCDF files.
