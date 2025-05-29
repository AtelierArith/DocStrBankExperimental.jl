```
ogr2ogr(indata, options=String[]; dest="/vsimem/tmp", kwargs...)
```

### Parameters

  * `indata` The source dataset.
  * `options` List of options (potentially including filename and open           options). The accepted options are the ones of the gdalwarp utility.
  * `kw` are kwargs that may contain the GMT region (-R), proj (-J), inc (-I) and `save=fname` options

### Returns

A GMT dataset, or a GDAL dataset (or nothing if file was writen on disk).
