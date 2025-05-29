```
fillnodata!(data::GItype; nodata=nothing, kwargs...)
```

Fill selected raster regions by interpolation from the edges.

### Args

  * `data`:  Input data. It can be a file name, a GMTgrid or GMTimage object.

### Kwargs

  * `nodata`: The nodata value that will be used to fill the regions. Otherwise use the `nodata` attribute of `indata`  if it exists, or NaN if none of the above were set.
  * band: the band number. Default is first layer in `indata`
  * maxdist: the maximum number of cels to search in all directions to find values to interpolate from. Default, fills all.
  * nsmooth: the number of 3x3 smoothing filter passes to run (0 or more).

### Returns

The modified input `data`
