```
set_band_names(filename::String, band_names::Vector)
```

Set the names of the bands in a raster dataset specified by the given filename.

# Arguments

  * `filename::String`: Path to the raster file. The file must be in a format supported by

GDAL. The data file is updated in place.

  * `band_names::Vector`: A vector of strings containing the new names for each band in the

raster dataset. The length of this vector must match the number of bands in the raster.
