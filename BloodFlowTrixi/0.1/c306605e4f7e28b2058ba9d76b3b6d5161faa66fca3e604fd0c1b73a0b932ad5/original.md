```
initial_condition_simple(x, t, eq::BloodFlowEquations1D; R0=2.0)
```

Generates a simple initial condition with a specified initial radius `R0`.

### Parameters

  * `x`: Position vector.
  * `t`: Time scalar.
  * `eq::BloodFlowEquations1D`: Instance of the blood flow model.
  * `R0`: Initial radius (default: `2.0`).

### Returns

State vector with zero initial area perturbation, zero flow rate, constant elasticity modulus, and reference area computed as `A_0 = \pi R_0^2`.

This initial condition is suitable for basic tests without complex dynamics.
