```
map_resample(map_map::Matrix, map_xx::Vector, map_yy::Vector,
             map_mask::BitMatrix, map_xx_new::Vector, map_yy_new::Vector)
```

Resample map with new grid.

**Arguments:**

  * `map_map`:    `ny` x `nx` 2D gridded map data
  * `map_xx`:     `nx` map x-direction (longitude) coordinates
  * `map_yy`:     `ny` map y-direction (latitude)  coordinates
  * `map_mask`    `ny` x `nx` mask for valid (not filled-in) map data
  * `map_xx_new`: `nx_new` map x-direction (longitude) coordinates to use for resampling
  * `map_yy_new`: `ny_new` map y-direction (latitude)  coordinates to use for resampling

**Returns:**

  * `map_map`:  `ny_new` x `nx_new` 2D gridded map data, resampled
  * `map_mask`: `ny_new` x `nx_new` mask for valid (not filled-in) map data, resampled
