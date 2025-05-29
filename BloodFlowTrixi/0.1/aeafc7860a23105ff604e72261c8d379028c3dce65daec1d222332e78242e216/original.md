```
boundary_condition_outflow(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations1D)
```

Implements the outflow boundary condition, assuming that there is no reflection at the boundary.

### Parameters

  * `u_inner`: State vector inside the domain near the boundary.
  * `orientation_or_normal`: Normal orientation of the boundary.
  * `direction`: Integer indicating the direction of the boundary.
  * `x`: Position vector.
  * `t`: Time.
  * `surface_flux_function`: Function to compute flux at the boundary.
  * `eq`: Instance of `BloodFlowEquations1D`.

### Returns

Computed boundary flux.
