```
coordinates(Integer, p::PointRecord)
coordinates(Integer, points, inds = :)
```

Obtain the “raw” x-, y-, and z-coordinate as a tuple of 32-bit integers. The meaning of these coordinates depends on a scaling and a coordinate reference system that are external to the point record.

The coordinates are read from a single point `p` or from the collection `points` at one or multiple indices `inds`, returning a vector of values in the latter case. The first argument also be used to specify a specific integer type for the coordinates.

See also: [`PointRecord`](@ref)
