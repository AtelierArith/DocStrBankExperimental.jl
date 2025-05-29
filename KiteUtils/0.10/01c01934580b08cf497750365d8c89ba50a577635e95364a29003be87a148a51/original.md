```
azn2azw(azimuth_north; upwind_dir = -π/2)
```

Calculate the azimuth in the wind reference frame. The `upwind_dir` is the direction the wind is coming from Zero is at north; clockwise positive. Default: Wind from west.

Returns:

  * Angle in radians. Zero straight downwind. Positive direction clockwise seen from above.
  * Valid range: -pi .. pi.
