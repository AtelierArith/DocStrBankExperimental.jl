```
friction(u, x, eq::BloodFlowEquations1D)
```

Calculates the friction term for the blood flow equations, which represents viscous resistance to flow along the artery wall.

### Parameters

  * `u`: State vector containing cross-sectional area and flow rate.
  * `x`: Position along the artery.
  * `eq::BloodFlowEquations1D`: Instance of the blood flow model.

### Returns

Friction coefficient as a scalar.
