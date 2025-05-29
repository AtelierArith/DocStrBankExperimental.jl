```
GeoRegion
```

Abstract supertype for geographical regions. All `GeoRegion` types contain the following fields:

  * `ID` - A `String` Type, the identifier for the GeoRegion.
  * `pID` - A `String` Type, the identifier for the parent GeoRegion.
  * `name` - A `String` Type, the full name of the GeoRegion.
  * `bound` - A vector of `Float` Types, defining the [North, South, East, West] boundaries of the GeoRegion.
  * `shape` - A vector of `Point2` (see [GeometryBasics.jl](https://github.com/JuliaGeometry/GeometryBasics.jl)) Types, defining a non-rectilinear shape of the GeoRegion
  * `geometry` - A `Polygon` Type (see [GeometryBasics.jl](https://github.com/JuliaGeometry/GeometryBasics.jl)), which is useful when doing checks on polygons using [GeometryOps.jl](https://github.com/JuliaGeo/GeometryOps.jl).
