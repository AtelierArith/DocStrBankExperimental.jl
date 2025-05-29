```
boundary_condition_slip_wall(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations1D)
```

Implements a slip wall boundary condition where the normal component of velocity is reflected.

### Parameters

  * `u_inner`: State vector inside the domain near the boundary.
  * `orientation_or_normal`: Normal orientation of the boundary.
  * `direction`: Integer indicating the direction of the boundary.
  * `x`: Position vector.
  * `t`: Time.
  * `surface_flux_function`: Function to compute flux at the boundary.
  * `eq`: Instance of `BloodFlowEquations1D`.

### Returns

Computed boundary flux at the slip wall.
