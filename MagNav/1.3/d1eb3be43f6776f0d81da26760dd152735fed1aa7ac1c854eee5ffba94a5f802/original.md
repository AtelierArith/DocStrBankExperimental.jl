```
map_fill!(mapS::Union{MapS,MapSd,MapS3D}; k::Int = 3)
```

Fill areas that are missing map data.

**Arguments:**

  * `mapS`: `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `k`:    (optional) number of nearest neighbors for knn

**Returns:**

  * `nothing`: `map` field within `mapS` is mutated with filled map data
