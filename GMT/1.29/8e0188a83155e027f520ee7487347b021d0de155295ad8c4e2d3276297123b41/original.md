```
xyzw2cube(fname::AbstractString; zcol::Int=4, datatype::DataType=Float32, proj4::String="", wkt::String="",
          epsg::Int=0, tit::String="", names::Vector{String}=String[], varnames::Vector{String}=String[])
```

or

```
xyzw2cube(D::GMTdataset; zcol::Int=4, datatype::DataType=Float32, tit::String="",
          names::Vector{String}=String[], varnames::Vector{String}=String[])
```

Convert data table containing a cube into a GMTgrid cube. The input data must contain a completelly filled 3D matrix and the data layout is guessed from file analysis (if it fails ... bad chance). 

### Parameters

  * `fname`: The filename of the cube in text format
  * `datatype`:  The data type where the data will be stored. The default is Float32.
  * `tit`:  A title string to describe this cube.
  * `proj4`:  A proj4 string for dataset SRS.
  * `wkt`:  Projection given as a WKT SRS.
  * `epsg`: Same as `proj` but using an EPSG code
  * `names`: used to give a description for each layer (also saved to file when using a GDAL function).
  * `varnames`: A string vector with the names of the variables in the cube. By default we get those from the column names (when available). Example: `varnames=["lon", "lat", "depth", "temp"]`.
  * `zcol`: The column number where the z values are stored. The default is 4. Use a higher number if the data set has more than 4 columns and you want to use one of those last columns as z values.

### Returns

A GMTgrid cube object.
