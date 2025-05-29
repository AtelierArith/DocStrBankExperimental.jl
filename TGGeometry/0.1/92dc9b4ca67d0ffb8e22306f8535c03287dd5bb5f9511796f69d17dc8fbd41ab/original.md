```
intersects(geom1, geom2)
```

Check if `geom1` and `geom2` intersect, as defined by DE-9IM [^de9im].

Specifically, this checks that the intersection of two geometries does not result in an empty set.

# Arguments

  * `geom1`: The first geometry.  May be any GeoInterface-compatible geometry.
  * `geom2`: The second geometry.  May be any GeoInterface-compatible geometry.

[^de9im]: the [Dimensionally Extended 9-Intersection Model](https://en.wikipedia.org/wiki/DE-9IM) that describes the relationship between two planar geometries.
