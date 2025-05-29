```
gdalshade(filename; kwargs...)
```

Create a shaded relief with the GDAL method (color image blended with shaded intensity).

  * kwargs hold the keyword=value to pass the arguments to `gdaldem hillshade`

Example:     I = gdalshade("hawaii_south.grd", C="faa.cpt", zfactor=4);

### Returns

A GMT RGB Image
