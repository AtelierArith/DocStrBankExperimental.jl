```
boundary_condition_pressure_in(u_inner, normal, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

Applies an inflow boundary condition with a prescribed pressure for the 2D blood flow model. This version does not use a specific direction parameter.

### Parameters

  * `u_inner`: Inner state vector at the boundary.
  * `normal`: Normal vector indicating the boundary direction.
  * `x`: Position vector at the boundary.
  * `t`: Time value.
  * `surface_flux_function`: Function to compute the surface flux.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Boundary flux as an `SVector`.
