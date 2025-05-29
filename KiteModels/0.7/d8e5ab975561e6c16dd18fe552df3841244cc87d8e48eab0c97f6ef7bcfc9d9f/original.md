```
calculate_rotational_inertia!(s::AKM, include_kcu::Bool=true, around_kcu::Bool=false)
```

Calculate the rotational inertia (Ixx, Ixy, Ixz, Iyy, Iyz, Izz) for a kite model from settings. Modifies the kitemodel by initialising the masses.

Parameters:

  * X: x-coordinates of the point masses.
  * Y: y-coordinates of the point masses.
  * Z: z-coordinates of the point masses.
  * M: masses of the point masses.
  * `include_kcu`: Include the kcu in the rotational intertia calculation?
  * `around_kcu`: Uses the kcu as the rotation point.

Returns:   The tuple  Ixx, Ixy, Ixz, Iyy, Iyz, Izz where:

  * Ixx: rotational inertia around the x-axis.
  * Ixy: rotational inertia around the xy-plane.
  * Ixz: rotational inertia around the xz-plane.
  * Iyy: rotational inertia around the y-axis.
  * Iyz: rotational inertia around the yz-plane.
  * Izz: rotational inertia around the z-axis.
