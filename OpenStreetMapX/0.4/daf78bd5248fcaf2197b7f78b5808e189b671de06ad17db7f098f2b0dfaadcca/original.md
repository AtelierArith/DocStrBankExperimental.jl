```
nodes_within_range(nodes::Dict{Int,T}, loc::T, node_list::AbstractSet{Int}, range::Float64 = Inf) where T<:(Union{OpenStreetMapX.ENU,OpenStreetMapX.ECEF})
```

Find nodes within range of a location using a subset of nodes
