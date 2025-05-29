```
source_term_simple(u, x, t, eq::BloodFlowEquations2D)
```

Computes a simple source term for the 2D blood flow model, including friction and curvature effects.

### Parameters

  * `u`: State vector.
  * `x`: Position vector.
  * `t`: Time value.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.

### Returns

Source term as an `SVector`.
