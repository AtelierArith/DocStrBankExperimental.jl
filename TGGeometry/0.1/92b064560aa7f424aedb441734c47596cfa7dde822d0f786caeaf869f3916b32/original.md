```
covers(geom1, geom2)
```

Check if `geom1` covers `geom2`, as defined by DE-9IM [^de9im].

This means that no points of `geom2` lie outside of `geom1`.

# Arguments

  * `geom1`: The first geometry.  May be any GeoInterface-compatible geometry.
  * `geom2`: The second geometry.  May be any GeoInterface-compatible geometry.

[^de9im]: the [Dimensionally Extended 9-Intersection Model](https://en.wikipedia.org/wiki/DE-9IM) that describes the relationship between two planar geometries.
