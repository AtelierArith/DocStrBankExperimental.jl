```
EPSG <: CoordinateReferenceSystemFormat

EPSG(input)
```

EPSG code representing a coordinate reference system from the EPSG spatial reference system registry.

String input must start with "EPSG:". `EPSG` can be converted to an `Int` or `String` using `convert`, or another `CoordinateReferenceSystemFormat` when ArchGDAL.jl is loaded.
