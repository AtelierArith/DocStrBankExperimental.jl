```
initial_condition_simple(x, t, eq::BloodFlowEquations2D; R0=2.0)
```

Defines a simple initial condition for the 2D blood flow model.

### Parameters

  * `x`: Position vector.
  * `t`: Initial time.
  * `eq::BloodFlowEquations2D`: Instance of `BloodFlowEquations2D`.
  * `R0`: Initial radius (default is 2.0).

### Returns

State vector as an `SVector`.
