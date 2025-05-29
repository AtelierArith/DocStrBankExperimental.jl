```
get_arrow(x::RealVector, y::RealVector, grid::VoronoiGrid)::RealVector
```

Return a vector from `y` to `x`. Equal to `x - y` on non-periodic domains.  For periodic rectangle, the shortest possible vector is returned.
