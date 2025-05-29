```
map_border(map_map::Matrix, map_xx::Vector, map_yy::Vector;
           inner::Bool       = true,
           sort_border::Bool = false,
           return_ind::Bool  = false)
```

Get map border from an unfilled map.

**Arguments:**

  * `map_map`:     `ny` x `nx` 2D gridded map data
  * `map_xx`:      `nx` map x-direction (longitude) coordinates
  * `map_yy`:      `ny` map y-direction (latitude)  coordinates
  * `inner`:       (optional) if true, get inner border, otherwise outer border
  * `sort_border`: (optional) if true, sort border data points sequentially
  * `return_ind`:  (optional) if true, return `ind`

**Returns:**

  * `yy`:  border y-direction (latitude)  coordinates
  * `xx`:  border x-direction (longitude) coordinates
  * `ind`: if `return_ind = true`, `BitMatrix` of border indices within `map_map`
