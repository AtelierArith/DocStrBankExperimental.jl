```
screenshot_to_GeoData(filename::String, Corner_LowerLeft, Corner_UpperRight; Corner_LowerRight=nothing, Corner_UpperLeft=nothing, Cartesian=false, UTM=false, UTMzone, isnorth=true, fieldname::Symbol=:colors)
```

Take a screenshot of Georeferenced image either a `lat/lon`, `x,y` (if `Cartesian=true`) or in UTM coordinates (if `UTM=true`) at a given depth or along profile and converts it to a `GeoData`, `CartData` or `UTMData` struct, which can be saved to Paraview

The lower left and upper right coordinates of the image need to be specified in tuples of `(lon,lat,depth)` or `(UTM_ew, UTM_ns, depth)`, where `depth` is negative inside the Earth (and in km).

The lower right and upper left corners can be specified optionally (to take non-orthogonal images into account). If they are not specified, the image is considered orthogonal and the corners are computed from the other two.

*Note*: if your data is in `UTM` coordinates you also need to provide the `UTMzone` and whether we are on the northern hemisphere or not (`isnorth`).
