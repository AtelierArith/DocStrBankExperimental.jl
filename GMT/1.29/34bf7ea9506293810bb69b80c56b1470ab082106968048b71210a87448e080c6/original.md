```
x_min, x_max, y_min, y_max, x_inc_or_z_min, y_inc_or_z_max = getregion(dataset; gridreg=false, sds=0, GMT=false)
```

Inquire the region extents of a file or GMTgrid, GMTimage, GMTdataset or GDAL dataset.

Options `gridreg` and `sds` are only for GDAL datasets. When `input` is a string (a file name) the default is to use GDAL and the region comes in 'pixel registration' by default. Use `gridreg=true` to force 'grid registration'. Still for `input` as string, use `GMT=true` to force the result to be given by `grdinfo`. An unfortunate consequence of using either GMT or GDAL to inquire a file/object is that the 5th and 6th outputs (only 4 when `input` is a GMTdataset) have different contents. It will be either `x_inc, y_inc` when reading with GDAL, and `z_min, z_max` when reading with GMT.
