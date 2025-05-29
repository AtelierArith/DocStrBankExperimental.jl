```
map_resample(mapS::MapS, map_xx_new::Vector, map_yy_new::Vector)
```

Resample map with new grid.

**Arguments:**

  * `mapS`:       `MapS` scalar magnetic anomaly map struct
  * `map_xx_new`: `nx_new` map x-direction (longitude) coordinates to use for resampling
  * `map_yy_new`: `ny_new` map y-direction (latitude)  coordinates to use for resampling

**Returns:**

  * `mapS`: `MapS` scalar magnetic anomaly map struct, resampled
