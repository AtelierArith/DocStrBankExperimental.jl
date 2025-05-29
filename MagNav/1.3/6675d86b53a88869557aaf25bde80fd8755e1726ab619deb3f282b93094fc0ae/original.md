```
map_border(mapS::Union{MapS,MapSd,MapS3D};
           inner::Bool       = true,
           sort_border::Bool = false,
           return_ind::Bool  = false)
```

Get map border from an unfilled map.

**Arguments:**

  * `mapS`:        `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `inner`:       (optional) if true, get inner border, otherwise outer border
  * `sort_border`: (optional) if true, sort border data points sequentially
  * `return_ind`:  (optional) if true, return `ind`

**Returns:**

  * `yy`:  border y-direction (latitude)  coordinates
  * `xx`:  border x-direction (longitude) coordinates
  * `ind`: if `return_ind = true`, `BitMatrix` of border indices within `map_map`
