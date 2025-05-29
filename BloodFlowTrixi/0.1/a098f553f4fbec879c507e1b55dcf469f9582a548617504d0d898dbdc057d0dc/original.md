```
boundary_condition_outflow(u_inner, orientation_or_normal, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

Applies an outflow boundary condition for the 2D blood flow model without reflecting any flux. This version does not use a specific direction parameter.

### Parameters

  * `u_inner`: Inner state vector at the boundary.
  * `orientation_or_normal`: Orientation index or normal vector indicating the boundary direction.
  * `x`: Position vector at the boundary.
  * `t`: Time value.
  * `surface_flux_function`: Function to compute the surface flux.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Boundary flux as an `SVector`.
