```
boundary_condition_pressure_in(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations1D)
```

Implements a pressure inflow boundary condition where the inflow pressure varies with time.

### Parameters

  * `u_inner`: State vector inside the domain near the boundary.
  * `orientation_or_normal`: Normal orientation of the boundary.
  * `direction`: Integer indicating the boundary direction.
  * `x`: Position vector.
  * `t`: Time scalar.
  * `surface_flux_function`: Function to compute flux at the boundary.
  * `eq`: Instance of `BloodFlowEquations1D`.

### Returns

Computed boundary flux with inflow pressure specified by:

$$
P_{in} = \begin{cases}
2 \times 10^4 \sin^2(\pi t / 0.125) & \text{if } t < 0.125 \\
0 & \text{otherwise}
\end{cases}
$$

The corresponding inflow area `A_{in}` is computed using the inverse pressure relation, and the boundary state is constructed accordingly.
