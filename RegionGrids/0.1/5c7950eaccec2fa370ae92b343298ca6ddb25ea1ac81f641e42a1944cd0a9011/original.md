```
UnstructuredGrid
```

A `UnstructuredGrid` is a `RegionGrid` that is created based on an unstructured grid often used in cubed-sphere or unstructured-mesh grids.

All `UnstructuredGrid` type will contain the following fields:

  * `lon` - A vector of `Float`s, defining the longitudes for each point in the RegionGrid that describe the region.
  * `lat` - A vector of `Float`s, defining the latitude for each point in the RegionGrid that describe the region.
  * `ipoint` - A Vector of `Int`s, defining the indices of the valid points from the original unstructured grid that were extracted into the RegionGrid.
