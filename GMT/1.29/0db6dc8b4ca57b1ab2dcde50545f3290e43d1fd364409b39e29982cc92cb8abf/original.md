```
gdalwrite(fname::AbstractString, data, opts=String[]; kwargs...)
```

Write a raster or a vector file to disk

  * `fname`: Output file name. If not explicitly selected via `opts` the used driver will be picked from the file extension.
  * `data`:  The data to be saved in file. It can be a GMT type or a GDAL dataset.
  * `opts`:  List of options. The accepted options are the ones of the gdal_translate or ogr2ogr utility.          This list can be in the form of a vector of strings, or joined in a simgle string.
  * `kwargs`: This options accept the GMT region (-R) and increment (-I)

Or

```
gdalwrite(cube::GItype, fname::AbstractString, v=nothing; dim_name::String="time", dim_units::String="")
```

Write a MxNxP `cube` object to disk as a multilayered file.

  * `cube`: A GMTgrid or GMTimage cube
  * `fname`: The file name where to save the `cube`
  * `v`: A vector with the coordinates of the Z layers (if omitted create one as 1:size(cube,3))
  * `dim_name`: The name of the variable of the $vertical$ dimension.
  * `dim_units`: The units of the `v` vector. If not provided, use the `cube.z_units` if exist (GMTgrid only)
