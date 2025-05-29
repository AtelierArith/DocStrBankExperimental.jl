```
struct CylindricalPoint{T} <: AbstractCoordinatePoint{T, Cylindrical}
```

Describes a three-dimensional point in cylindrical coordinates. 

## Fields

  * `r`: Radius (in m).
  * `φ`: Polar angle (in rad).
  * `z`: `z`-coordinate (in m).

!!! note
    `φ == 0` corresponds to the `x`-axis in the Cartesian coordinate system.


See also [`CartesianPoint`](@ref).
