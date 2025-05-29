```
D = polygonize(data::GItype; kwargs...) -> Vector{GMTdataset}
```

This method, which uses the GDAL GDALPolygonize function, creates vector polygons for all connected regions of pixels in the raster sharing a common pixel/cell value. The input may be a grid or an image. This function can be rather slow as it picks lots of polygons in pixels with slightly different values at transitions between colors. Its natural use is to digitize masks images.

### Args

  * `data`: Input data. It can be a GMTgrid or GMTimage object.

### Kwargs

  * `min, nmin, npixels or ncells`: The minimum number of cells/pixels for a polygon to be retained.   Default is 1. This can be set to filter out small polygons.
  * `min_area`: Minimum area in m2 for a polygon to be retained. This option takes precedence over the one   above that is based in the counting of cells. Note also that this is an approximate value because at this   point we still don't know exactly the latitudes of the polygons.
  * `max_area`: Maximum area in m2 for a polygon to be retained.
  * `simplify`: Apply the Douglas-Peucker line simplification algorithm to the poligons. Provide a tolerence   in meters. For example: `simplify=0.5`. But be warned that this is a risky option since a too large tolerance   can lead to loss of otherwise good polygons. A good rule of thumb is to use the cell size for the tolerance.   And in fact that is what we do when using `simplify=:auto`.
  * `sort`: If true, will sort polygons by pixel count. Default is the order that GDAL decides internally.
