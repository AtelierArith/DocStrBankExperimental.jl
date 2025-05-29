```
G = gdalgrid(indata, method::StrSymb="", options=String[]; dest="/vsimem/tmp", kw...)
```

### Parameters

  * `indata`: The source dataset. It can be a file name, a GMTdataset, a Mx3 matrix or a GDAL dataset
  * `method`: The interpolation method name. One of "invdist", "invdistnn", "average", "nearest", "linear",           "minimum", "maximum", "range", "count", "average*distance", "average*distance_pts".
  * `options`: List of options. The accepted options are the ones of the gdal_grid utility.           This list can be in the form of a vector of strings, or joined in a single string.
  * `kwargs`: The `kwargs` may also contain the GMT region (-R), inc (-I) and `save=fname` options.

### Returns

A GMTgrid or a GDAL dataset (or nothing if file was writen on disk). To force the return of a GDAL dataset use the option `gdataset=true`.
