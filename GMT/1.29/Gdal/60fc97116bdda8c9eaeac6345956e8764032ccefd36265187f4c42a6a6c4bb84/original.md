```
GI = fillnodata(data::String; nodata=nothing, kwargs...) -> GMTgrid or GMTimage
```

Fill selected raster regions by interpolation from the edges.

### Parameters

  * `data`:  Input data. The file name of a grid or image that can be read with `gmtread`.
  * `nodata`: The nodata value that will be used to fill the regions. Otherwise use the `nodata` attribute of `indata`  if it exists, or NaN if none of the above were set.
  * `kwargs`:

      * band: the band number. Default is first layer in `indata`
      * maxdist: the maximum number of cels to search in all directions to find values to interpolate from. Default, fills all.
      * nsmooth: the number of 3x3 smoothing filter passes to run (0 or more).

### Returns

A GMTgrid or GMTimage object with the `band` nodata values filled by interpolation.
