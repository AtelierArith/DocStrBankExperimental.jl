```
map_chessboard(mapSd::MapSd, alt::Real;
               down_cont::Bool = true,
               dz              = 5,
               down_max        = 150,
               α               = 200)
```

Perform the `chessboard method`, which upward (and possibly downward) continues a map to multiple altitudes to create a 3D map, then vertically interpolates at each horizontal grid point.

Reference: Cordell, Phillips, & Godson, U.S. Geological Survey Potential-Field Software Version 2.0, 1992.

**Arguments:**

  * `mapSd`:     `MapSd` scalar magnetic anomaly map struct
  * `alt`:       final map altitude after upward continuation [m]
  * `down_cont`: (optional) if true, downward continue if needed
  * `dz`:        (optional) upward continuation step size [m]
  * `down_max`:  (optional) maximum downward continuation distance [m]
  * `α`:         (optional) regularization parameter for downward continuation

**Returns:**

  * `mapS`: `MapS` scalar magnetic anomaly map struct
