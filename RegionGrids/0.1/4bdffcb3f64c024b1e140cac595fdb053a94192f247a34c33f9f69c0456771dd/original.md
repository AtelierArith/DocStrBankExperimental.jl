```
GeneralizedGrid
```

A `GeneralizedGrid` is a `RegionGrid` that is created based on longitude/latitude grids that are **not** rectilinear - this can range from curvilinear grids to unstructured grids. It has its own subtypes: `RegionMask` and `VectorMask`.

All `GeneralizedGrid` type will contain the following fields:

  * `lon` - A Matrix of `Float`s, defining the longitudes for each point in the RegionGrid that describe the region.
  * `lat` - A Matrix of `Float`s, defining the latitude for each point in the RegionGrid that describe the region.
  * `ilon` - A Vector of `Int`s, defining the indices used to extract the longitude vector from the input longitude vector.
  * `ilat` - A Vector of `Int`s, defining the indices used to extract the latitude vector from the input latitude vector.
  * `mask` - An Array of NaNs and 1s, defining the gridpoints in the RegionGrid where the data is valid.
