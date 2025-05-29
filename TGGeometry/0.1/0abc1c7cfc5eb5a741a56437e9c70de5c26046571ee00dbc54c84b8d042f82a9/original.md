```
coveredby(geom1, geom2)
```

Check if `geom1` is covered by `geom2`, as defined by DE-9IM [^de9im].

This means that no points of `geom1` lie outside of `geom2`.  

Equivalent to `covers(geom2, geom1)` - argument order reversed.

# Arguments

  * `geom1`: The first geometry.  May be any GeoInterface-compatible geometry.
  * `geom2`: The second geometry.  May be any GeoInterface-compatible geometry.

[^de9im]: the [Dimensionally Extended 9-Intersection Model](https://en.wikipedia.org/wiki/DE-9IM) that describes the relationship between two planar geometries.
