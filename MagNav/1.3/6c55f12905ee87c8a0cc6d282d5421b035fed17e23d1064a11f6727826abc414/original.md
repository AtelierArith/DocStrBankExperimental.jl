```
downward_L(map_map::Matrix, dx, dy, dz, α::Vector;
           map_mask::BitMatrix = map_params(map_map)[2],
           expand::Bool        = true)
```

Downward continuation using a sequence of regularization parameters to create a characteristic L-curve. The optimal regularization parameter is at a local minimum on the L-curve, which is a local maximum of curvature. The global maximum of curvature may or may not be the optimal regularization parameter.

**Arguments:**

  * `map_map`:   `ny` x `nx` 2D gridded map data
  * `dx`:        x-direction map step size [m]
  * `dy`:        y-direction map step size [m]
  * `dz`:        z-direction upward/downward continuation distance [m]
  * `α`:        (geometric) sequence of regularization parameters
  * `map_mask`: (optional) `ny` x `nx` mask for valid (not filled-in) map data
  * `expand`:   (optional) if true, expand map temporarily to reduce edge effects

**Returns:**

  * `norms`: L-infinity norm of difference between sequential D.C. solutions
