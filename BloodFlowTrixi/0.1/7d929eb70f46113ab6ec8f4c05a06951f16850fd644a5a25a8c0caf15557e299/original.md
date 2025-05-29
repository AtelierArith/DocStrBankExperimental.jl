```
flux_nonconservative(u_ll, u_rr, orientation::Integer, eq::BloodFlowEquations1D)
```

Computes the non-conservative flux for the model, used for handling discontinuities in pressure.

### Parameters

  * `u_ll`: Left state vector.
  * `u_rr`: Right state vector.
  * `orientation::Integer`: Orientation index.
  * `eq`: Instance of `BloodFlowEquations1D`.

### Returns

Non-conservative flux vector.
