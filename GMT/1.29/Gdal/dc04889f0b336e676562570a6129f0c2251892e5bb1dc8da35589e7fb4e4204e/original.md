```
gdaldem(dataset, method, options=String[]; dest="/vsimem/tmp", color=name|GMTcpt, kw...)
```

Tools to analyze and visualize DEMs.

### Parameters

  * `dataset` The source dataset.
  * `method` the processing to apply (one of "hillshade", "slope",   "aspect", "color-relief", "TRI", "TPI", "Roughness").
  * `options` List of options (potentially including filename and open options).   The accepted options are the ones of the gdaldem utility.

# Keyword Arguments

  * `color` color file (mandatory for "color-relief" processing, should be empty otherwise).  If `color` is just a CPT name we compute a CPT from it and the input grid.
  * `kw...` keyword=value arguments when `method` is hillshade.

### Returns

A GMT grid or Image, or a GDAL dataset (or nothing if file was writen on disk).
