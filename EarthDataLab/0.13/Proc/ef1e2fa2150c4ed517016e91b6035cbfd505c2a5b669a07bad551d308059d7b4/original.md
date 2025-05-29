```
cubefromshape(shapepath, refcube; samplefactor=nothing, labelsym = nothing, T=Int32)
```

Read the shapefile at `shapepath`, which is required to contain a list of polygons to construct a cube. The polygons will be *rasterized* to the same grid and bounding box as the reference data cube `refcube`. If the shapefile comes with additional labels in a .dbf file, the labels can be mapped to the respective field codes by providing the label to choose as a symbol. If a `samplefactor` is supplied, the polygons will be rasterized on an n-times higher resolution and the fraction of area within each polygon will be returned.
