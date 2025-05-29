```
O = gd2gmt(dataset; band=0, bands=[], sds=0, pad=0)
```

Convert a GDAL raster dataset into either a GMTgrid (if type is Int16 or Float) or a GMTimage type Use `band` to select a single band of the dataset. When you know that the dataset contains several bands of an image, use the kwarg `bands` with a vector the wished bands. By default it reads all bands of the image or grid object.

When DATASET is a string it may contain the file name or the name of a subdataset. In former case you can use the kwarg `sds` to selec the subdataset numerically. Alternatively, provide the full `sds` name. For files with `sds` with a scale_factor (e.g. MODIS data), that scale is applyied automaticaly.

### Examples:

G = gd2gmt("AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc", sds=1);

Or

G = gd2gmt("SUBDATASET*1*NAME=NETCDF:AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc:sst");

Or

G = gd2gmt("NETCDF:AQUA_MODIS.20210228.L3m.DAY.NSST.sst.4km.NRT.nc:sst");
