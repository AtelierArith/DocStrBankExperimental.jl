```
CountryBorder{T} <: Geometry{🌐,LATLON{T}}
```

Structure representings the coordinates of the borders of a country (based on the NaturalEarth database).  `T` is the floating point precision of the borders coordinates, and defaults to Float32.

This structure holds the borders in both LatLon and Cartesian2D, to allow faster comparison with flattening approximation of the LatLon coordinates.

# Fields

  * `admin::String`: The name of the country, i.e. the ADMIN entry in the GeoTable.
  * `table_idx::Int`: The index of the country in the original GeoTable.
  * `valid_polyareas::BitVector`: The indices of skipped PolyAreas in the original MultiPolygon of the country.
  * `resolution::Int`: The resolution of the underlying border sampling from the NaturalEarth dataset.
  * `latlon::MULTI_LATLON{T}`: The borders in LatLon CRS.
  * `cart::MULTI_LATLON{T}`: The borders in Cartesian2D CRS.
