```
MixedKernelGradientCorrection()
```

Combines [`GradientCorrection`](@ref) and [`KernelCorrection`](@ref), which results in a 1st-order-accurate SPH method (see [Bonet, 1999](@cite Bonet1999)).

# Notes:

  * Stability issues, especially when particles separate into small clusters.
  * Doubles the computational effort.
