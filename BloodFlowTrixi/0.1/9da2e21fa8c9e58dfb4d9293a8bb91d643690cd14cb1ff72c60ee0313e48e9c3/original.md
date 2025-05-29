```
boundary_condition_slip_wall(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

Applies a slip-wall boundary condition for the 2D blood flow model by reflecting the normal component of the velocity at the boundary.

### Parameters

  * `u_inner`: Inner state vector at the boundary.
  * `orientation_or_normal`: Orientation index or normal vector indicating the boundary direction.
  * `direction`: Index indicating the spatial direction (1 for ( \theta )-direction, otherwise ( s )-direction).
  * `x`: Position vector at the boundary.
  * `t`: Time value.
  * `surface_flux_function`: Function to compute the surface flux.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Boundary flux as an `SVector`.
