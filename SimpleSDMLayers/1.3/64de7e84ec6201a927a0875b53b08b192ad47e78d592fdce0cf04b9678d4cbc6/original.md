```
SDMLayer{T}
```

Defines a layer of geospatial information.

The type has two data fields:

  * **grid**: a `Matrix` of type `T`
  * **indices**: a `BitMatrix` to see which positions are valued

Each *row* in the `grid` field represents a slice of the raster of equal *northing*, *i.e.* the information is laid out in the matrix as it would be represented on a map once displayed. Similarly, columns have the same *easting*.

The geospatial information is represented by three positional fields:

  * **x** and **y**: two tuples, indicating the coordinates of the *corners* alongside the *x* and *y* dimensions (e.g. easting/northing) - the default values are `(-180., 180.)` and `(-90., 90.)`, which represents the entire surface of the globe in WGS84
  * **crs**: any `String` representation of the CRS which can be handled by `Proj.jl` - the default is  `"+proj=longlat +datum=WGS84 +no_defs"`, which represents a latitude/longitude coordinate system
