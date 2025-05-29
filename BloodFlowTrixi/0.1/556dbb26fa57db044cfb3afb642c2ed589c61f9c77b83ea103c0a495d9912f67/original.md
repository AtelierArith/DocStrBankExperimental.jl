```
flux_nonconservative(u_ll, u_rr, normal, eq::BloodFlowEquations2D)
```

Computes the non-conservative flux for the 2D blood flow model based on a normal vector.

### Parameters

  * `u_ll`: Left state vector.
  * `u_rr`: Right state vector.
  * `normal`: Normal vector indicating the direction of the flux.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Non-conservative flux vector.
