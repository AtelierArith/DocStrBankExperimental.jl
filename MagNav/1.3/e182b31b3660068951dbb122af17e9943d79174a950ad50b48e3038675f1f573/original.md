```
map_chessboard!(map_map::Matrix, map_alt::Matrix, map_xx::Vector,
                map_yy::Vector, alt::Real;
                down_cont::Bool = true,
                dz              = 5,
                down_max        = 150,
                α               = 200)
```

Perform the `chessboard method`, which upward (and possibly downward) continues a map to multiple altitudes to create a 3D map, then vertically interpolates at each horizontal grid point.

Reference: Cordell, Phillips, & Godson, U.S. Geological Survey Potential-Field Software Version 2.0, 1992.

**Arguments:**

  * `map_map`:   `ny` x `nx` 2D gridded target (e.g., magnetic) map data on [m] grid
  * `map_alt`:   `ny` x `nx` 2D gridded altitude map data [m] on [m] grid
  * `map_xx`:    `nx` map x-direction (longitude) coordinates [m]
  * `map_yy`:    `ny` map y-direction (latitude)  coordinates [m]
  * `alt`:       final map altitude after upward continuation [m]
  * `down_cont`: (optional) if true, downward continue if needed, only used if `up_cont = true`
  * `dz`:        (optional) upward continuation step size [m]
  * `down_max`:  (optional) maximum downward continuation distance [m]
  * `α`:         (optional) regularization parameter for downward continuation

**Returns:**

  * `nothing`: `map_map` is mutated with upward continued map data
