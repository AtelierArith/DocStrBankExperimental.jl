```
gdalread(fname::AbstractString, opts=String[]; gdataset=false, kwargs...)
```

Read a raster or a vector file from a disk file and return the result either as a GMT type (the default) or a GDAL dataset.

  * `fname`: Input data. It can be a file name, a GMTgrid or GMTimage object or a GDAL dataset
  * `opts`:  List of options. The accepted options are the ones of the gdal_translate utility.          This list can be in the form of a vector of strings, or joined in a simgle string.
  * `gdataset`: If set to `true` forces the return of a GDAL dataset instead of a GMT type.
  * `kwargs`: This options accept the GMT region (-R) and increment (-I)

### Returns

A GMT grid/image or a GDAL dataset
