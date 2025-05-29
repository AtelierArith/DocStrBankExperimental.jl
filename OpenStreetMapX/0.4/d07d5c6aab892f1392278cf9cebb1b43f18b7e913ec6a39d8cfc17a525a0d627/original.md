```
nodes_within_range(nodes::Dict{Int,T},loc::T, m::OpenStreetMapX.MapData, range::Float64 = Inf) where T <:(Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF})
```

Find vertices of a routing network within range of a location
