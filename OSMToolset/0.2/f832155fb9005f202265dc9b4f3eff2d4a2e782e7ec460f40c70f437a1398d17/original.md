```
NodeSpatIndex(nodes::AbstractVector{Int64}, llas::AbstractVector{LLA}, refLLA::LLA; node_range::Number=100.0)
```

Create a spatial index for `nodes` having `llas` LLA coordinates using `refLLA` as the reference for ENU coordinates with the given `node_range` in meters.
