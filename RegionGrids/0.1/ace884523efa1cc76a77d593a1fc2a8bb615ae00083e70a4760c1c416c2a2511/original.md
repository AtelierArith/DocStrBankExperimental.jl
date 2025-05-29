```
RectilinearGrid <: RegionGrid
```

A `RectilinearGrid` is a `RegionGrid` that is created based on rectilinear longitude/latitude grids. It has its own subtypes: `RectGrid`, `TiltGrid` and `PolyGrid`.

All `RectilinearGrid` types contain the following fields:

  * `lon` - A Vector of `Float`s, defining the longitude vector describing the region.
  * `lat` - A Vector of `Float`s, defining the latitude vector describing the region.
  * `ilon` - A Vector of `Int`s, defining the indices used to extract the longitude vector from the input longitude vector.
  * `ilat` - A Vector of `Int`s, defining the indices used to extract the latitude vector from the input latitude vector.
  * `mask` - An Array of NaNs and 1s, defining the gridpoints in the RegionGrid where the data is valid.
