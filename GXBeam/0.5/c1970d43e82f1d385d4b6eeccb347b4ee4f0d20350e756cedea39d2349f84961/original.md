```
discretize_beam(start, stop, discretization; frame, curvature)
```

Discretize a beam from `start` to `stop` according to the discretization provided in  `discretization`.

Return the lengths, endpoints, midpoints, and reference frame of the beam elements.

# Arguments

  * `start`: Beam starting point
  * `stop`: Beam ending point
  * `discretization`: Number of beam elements, or the normalized endpoints of each beam       element, with values ranging from 0 to 1.

# Keyword Arguments

  * `frame`: Reference frame at the start of the beam element, represented by a 3x3      transformation matrix from the undeformed local frame to the body frame.
  * `curvature`: curvature vector
