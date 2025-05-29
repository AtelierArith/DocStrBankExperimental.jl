```
TiltRegion <: GeoRegion
```

A **tilted** rectangular region on a rectilinear grid. Defined by:

  * the (lon,lat) coordinates of its centre.
  * the width in both the longitude and latitude directions (pre-rotation).
  * the angle of tilt in degrees (clockwise).

In addition to all the fields common to the `GeoRegion` `abstract type`, `TiltRegion`s will also contain the following field:

  * `tilt` : A vector of `Float` Types, containing [X,Y,ΔX,ΔY,θ], where:

      * `X`  : A `Float` Type, the longitude coordinate of region centre.
      * `Y`  : A `Float` Type, the latitude coordinate of region centre.
      * `θ`  : A `Float` Type, the angle-tilt of rectangular region in **degrees** in the clockwise direction.
      * `ΔX` : A `Float` Type, the half-width in longitude coordinates (before tilting).
      * `ΔY` : A `Float` Type, the half-width in latitude coordinates (before tilting).
