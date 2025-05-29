```
power(sol,sys,bodyi;include_freestream=false)
```

Calculate the history of the total rate of work done by the flow on body `bodyi` (or on the flow by the body, if negative) from the computational solution `sol` of system `sys`. If `freestream=false` (default), then the free stream is not subtracted from the translational velocity in the calculation. If it is `true`, then the translational part of power is based on translational velocity minus the free stream (i.e., a reference frame at rest at infinity).
