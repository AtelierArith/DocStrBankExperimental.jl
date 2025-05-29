```
gdalwarp(indata, options=String[]; dest="/vsimem/tmp", kwargs...)
```

Image/Grid reprojection and warping function.

### Args

  * `indata`:  Input data. It can be a file name, a GMTgrid or GMTimage object or a GDAL dataset
  * `options`: List of options. The accepted options are the ones of the gdal_translate utility.           This list can be in the form of a vector of strings, or joined in a single string.           The accepted options are the ones of the gdalwarp utility.
  * `kwargs`: Besides what was mentioned above one can also use `meta=metadata`, where `metadata`           is a string vector with the form "NAME=...." for each of its elements. This data           will be recognized by GDAL as Metadata.           The `kwargs` may also contain the GMT region (-R), proj (-J), inc (-I) and `save=fname` options.

### Returns

A GMT grid or Image, or a GDAL dataset (or nothing if file was writen on disk).
