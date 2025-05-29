```
XPRS_MIPRESTARTFACTOR
```

Branch and Bound: Fine tune initial conditions to trigger an in-tree restart. (double)

Use a value > 1 to increase the aggressiveness with which the Optimizer restarts. Use a value < 1 to relax the aggressiveness with which the Optimizer restarts. Note that this control does not affect the initial condition on the gap, which must be set separately.

Default value: `1.0`

Domain: (0,+INF]
