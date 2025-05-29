```
DubinsManeuver3D struct
```

This struct contains all necessary information about the maneuver.

  * qi - initial configuration (x, y, z, heading, pitch)
  * qf - final configuration (x, y, z, heading, pitch)
  * rhomin - minimum turning radius
  * pitchlims - limits of the pitch angle [pitch*min, pitch*max]  where pitch_min < 0.0
  * path - array containing horizontal and vertical Dubins paths
  * length - total length of the 3D maneuver
