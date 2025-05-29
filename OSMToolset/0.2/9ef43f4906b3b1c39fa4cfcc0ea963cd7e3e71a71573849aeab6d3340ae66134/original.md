```
NodeSpatIndex(nodes::AbstractVector{Int64}, lattitudes::AbstractVector{Float64}, longitudes::AbstractVector{Float64}, refLLA::LLA=LLA(mean(lattitudes), mean(longitudes)); node_range::Number=100.0)
```

Create a spatial index for `nodes` having `lattitudes` and `longitudes` using `refLLA` as the reference for ENU coordinates with the given `node_range` in meters.
