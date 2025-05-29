```
ds = gmt2gd(GI)
```

Create GDAL dataset from the contents of GI that can be either a Grid or an Image

```
ds = gmt2gd(D, save="", geometry="")
```

Create GDAL dataset from the contents of D, which can be a GMTdataset, a vector of GMTdataset ir a MxN array. The `save` keyword instructs GDAL to save the contents as an OGR file. Format is determined by file estension. `geometry` can be a string with "polygon", where file will be converted to polygon/multipolygon depending on `D` is a single or a multi-segment object, or "point" to convert to a multipoint geometry.
