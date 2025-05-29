```
Assembly(points, start, stop; kwargs...)
```

Construct an assembly of connected nonlinear beam elements.  Beam lengths and midpoints  may be manually specified in case beam elements are curved rather than straight.

# Arguments

  * `points`: Array of all beam element endpoints
  * `start`: Array containing point indices where each beam element starts
  * `stop`: Array containing point indices where each beam element stops

# Keyword Arguments

  * `frames`: Array of (3 x 3) tranformation matrices for each beam element.      Transforms from the local undeformed beam frame to the global frame.       Defaults to the identity matrix.
  * `compliance`: Array of (6 x 6) compliance matrices for each beam element.      Defaults to `zeros(6,6)` for each beam element.
  * `mass`: Array of (6 x 6) mass matrices for each beam element.       Defaults to `zeros(6,6)` for each beam element.
  * `damping`: Array of (6) structural damping coefficients for each beam element.       Defaults to `fill(0.01, 6)` for each beam element.
  * `lengths`: Array containing the length of each beam element.      Defaults to the distance between beam endpoints.
  * `midpoints`: Array containing the midpoint of each beam element.      Defaults to the average of the beam element endpoints.
