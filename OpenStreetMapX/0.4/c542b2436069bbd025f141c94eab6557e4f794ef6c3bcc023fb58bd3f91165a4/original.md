```
latlon(m::MapData,map_g_point_id::Int64)::Tuple{Float64, Float64}
```

Returns a tuple of lattitute and longitude for a given graph node identifier `map_g_point_id` in graph `m.g` (i.e. `map_g_point_id ∈ 1:nv(m.g)`).
