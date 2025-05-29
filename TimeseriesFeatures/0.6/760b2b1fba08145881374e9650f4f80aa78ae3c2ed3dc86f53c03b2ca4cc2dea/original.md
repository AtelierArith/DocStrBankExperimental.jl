```
RAD(x, τ=1, doAbs=true)
```

Compute the rescaled auto-density, a metric for inferring the distance to criticality that is insensitive to uncertainty in the noise strength. Calibrated to experiments on the Hopf bifurcation with variable and unknown measurement noise.

Inputs:     x:      The input time series (vector).     doAbs:  Whether to centre the time series at 0 then take absolute values (logical flag)     τ:      The embedding and differencing delay in units of the timestep (integer), or :τ

Outputs:     f:      The RAD feature value
