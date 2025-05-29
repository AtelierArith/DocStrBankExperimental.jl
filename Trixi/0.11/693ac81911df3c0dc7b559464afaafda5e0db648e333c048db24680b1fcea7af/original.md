```
boundary_condition_slip_wall(u_inner, normal_direction, x, t, surface_flux_function,
                             equations::ShallowWaterEquations2D)
```

Create a boundary state by reflecting the normal velocity component and keep the tangential velocity component unchanged. The boundary water height is taken from the internal value. For details see Section 9.2.5 of the book:

  * Eleuterio F. Toro (2001) Shock-Capturing Methods for Free-Surface Shallow Flows 1st edition ISBN 0471987662
