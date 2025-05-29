```
flux_nonconservative(u_ll, u_rr, orientation::Integer, eq::BloodFlowEquations2D)
```

Computes the non-conservative flux for the 2D blood flow model based on the orientation.

### Parameters

  * `u_ll`: Left state vector.
  * `u_rr`: Right state vector.
  * `orientation::Integer`: Direction index for the flux (1 for ( \theta )-direction, otherwise ( s )-direction).
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Non-conservative flux vector.
