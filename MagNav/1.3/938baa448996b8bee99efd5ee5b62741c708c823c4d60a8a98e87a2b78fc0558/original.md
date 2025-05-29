```
vector_fft(map_map::Matrix, dx, dy, D, I)
```

Get potential field (i.e., magnetic anomaly field) map vector components using declination and inclination.

**Arguments:**

  * `map_map`: `ny` x `nx` 2D gridded map data
  * `dx`:      x-direction map step size [m]
  * `dy`:      y-direction map step size [m]
  * `D`:       map declination (Earth core field) [rad]
  * `I`:       map inclination (Earth core field) [rad]

**Returns:**

  * `Bx, By, Bz`: map vector components
