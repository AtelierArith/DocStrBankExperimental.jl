```
map_fill(map_map::Matrix, map_xx::Vector, map_yy::Vector; k::Int = 3)
```

Fill areas that are missing map data.

**Arguments:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `map_xx`:  `nx` map x-direction (longitude) coordinates
  * `map_yy`:  `ny` map y-direction (latitude)  coordinates
  * `k`:       (optional) number of nearest neighbors for knn

**Returns:**

  * `map_map`: `ny` x `nx` 2D gridded map data, filled
