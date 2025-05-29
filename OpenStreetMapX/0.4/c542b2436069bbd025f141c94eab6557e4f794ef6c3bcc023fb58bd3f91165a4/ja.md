```
latlon(m::MapData,map_g_point_id::Int64)::Tuple{Float64, Float64}
```

与えられたグラフノード識別子 `map_g_point_id` に対して、グラフ `m.g` の緯度と経度のタプルを返します（すなわち、`map_g_point_id ∈ 1:nv(m.g)`）。
