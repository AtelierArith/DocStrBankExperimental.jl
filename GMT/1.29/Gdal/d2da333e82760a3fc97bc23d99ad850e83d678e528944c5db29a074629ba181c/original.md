```
gdaltranslate(indata, options=String[]; dest="/vsimem/tmp", kwargs...)
```

Convert raster data between different formats.

Operations provided by the GDAL 'gdal_translate' tool. Namely sub-region extraction and resampling. The `kwargs` options accept the GMT region (-R), increment (-I), target SRS (-J). Any of the keywords `outgrid`, `outfile` or `save` = outputname options to make this function save the result on  a file designated by 'outputname'. The file format is picked from the 'outputname' file extension. When no output file name is provided it returns a GMT object (either a grid or an image, depending on the input type). To force the return of a GDAL dataset use the option `gdataset=true`.

### Args

  * `indata`: Input data. It can be a file name, a GMTgrid or GMTimage object or a GDAL dataset
  * `options`: List of options. The accepted options are the ones of the gdal_translate utility.           This list can be in the form of a vector of strings, or joined in a single string.

### Kwargs

  * `meta=metadata`, where `metadata` is a string vector with the form "NAME=...." for each of its elements. This data will be recognized by GDAL as Metadata.

The `kwargs` may also contain the GMT region (-R), proj (-J), inc (-I) and `save=fname` options.

### Returns

A GMT grid or Image, or a GDAL dataset (or nothing if file was writen on disk).
