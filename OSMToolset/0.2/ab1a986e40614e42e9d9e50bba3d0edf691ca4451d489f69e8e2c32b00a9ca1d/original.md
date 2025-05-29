```
NodeSpatIndex(nodes::AbstractVector{Int64}, enus::AbstractVector{ENU}, refLLA::LLA; node_range::Number=100.0)
```

Create a spatial index for `nodes` having `enus` ENU coordinates using `refLLA` as the reference for ENU coordinates with the given `node_range` in meters.
