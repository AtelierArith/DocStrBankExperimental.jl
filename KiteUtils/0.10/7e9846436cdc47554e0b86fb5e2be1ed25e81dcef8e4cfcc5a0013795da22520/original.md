```
calculate_rotational_inertia(X::Vector, Y::Vector, Z::Vector, M::Vector,  
      around_center_of_mass::Bool=true, rotation_point::Vector=[0, 0, 0])
```

Calculate the rotational inertia (Ixx, Ixy, Ixz, Iyy, Iyz, Izz) of a collection of point masses around a point.  By default this point is the center of mass which will be calculated, but any point can be given to rotation_point.

Parameters:

  * X: x-coordinates of the point masses.
  * Y: y-coordinates of the point masses.
  * Z: z-coordinates of the point masses.
  * M: masses of the point masses.
  * `around_center_of_mass`: Calculate the rotational inertia around the center of mass?
  * `rotation_point`: Rotation point used if not rotating around the center of mass.

Returns:   The tuple  Ixx, Ixy, Ixz, Iyy, Iyz, Izz where:

  * Ixx: rotational inertia around the x-axis.
  * Ixy: rotational inertia around the xy-plane.
  * Ixz: rotational inertia around the xz-plane.
  * Iyy: rotational inertia around the y-axis.
  * Iyz: rotational inertia around the yz-plane.
  * Izz: rotational inertia around the z-axis.
