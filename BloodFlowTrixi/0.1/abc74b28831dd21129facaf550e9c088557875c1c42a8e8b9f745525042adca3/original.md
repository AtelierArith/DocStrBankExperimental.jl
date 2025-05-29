```
source_term_simple(u, x, t, eq::BloodFlowEquations1D)
```

Computes a simple source term for the blood flow model, focusing on frictional effects.

### Parameters

  * `u`: State vector containing area perturbation, flow rate, elasticity modulus, and reference area.
  * `x`: Position vector.
  * `t`: Time scalar.
  * `eq::BloodFlowEquations1D`: Instance of the blood flow model.

### Returns

Source terms vector where:

  * `s_1 = 0` (no source for area perturbation).
  * `s_2` represents the friction term given by `s_2 = \frac{2 \pi k Q}{R A}`.

Friction coefficient `k` is computed using the `friction` function, and the radius `R` is obtained using the `radius` function.
