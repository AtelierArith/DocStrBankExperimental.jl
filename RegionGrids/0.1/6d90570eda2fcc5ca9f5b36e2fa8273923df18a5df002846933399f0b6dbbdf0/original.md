```
RegionGrid
```

Abstract supertype for geographical region gridded information. All `RegionGrids` will contain the following fields:

  * `lon` - A Vector or Matrix of `Float`s, defining the longitude grids describing the region.
  * `lat` - A Vector or Matrix of `Float`s, defining the latitude grids describing the region.
  * `weights` - An Vector or Matrix of `Float`s, defining the latitude-weights of each valid point in the grid. Will be NaN if outside the bounds of the GeoRegion used to define this RectilinearGrid.
  * `X` - A Vector or Matrix of `Float`s, defining the X-coordinates (in meters) of each point in the "derotated" RegionGrid about the centroid for the shape of the GeoRegion.
  * `Y` - A Vector or Matrix of `Float`s, defining the Y-coordinates (in meters) of each point in the "derotated" RegionGrid about the centroid for the shape of the GeoRegion.
  * `θ` - A `Float` storing the information on the angle (in degrees) about which the data was rotated in the anti-clockwise direction. Mathematically, it is `rotation - geo.θ`.
