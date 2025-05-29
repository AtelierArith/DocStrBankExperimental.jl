```
SimpleAdaptiveStepper(dx; dtmax = 0.1, dtmin = 1e-10)
```

Creates a [`TimeSteppingStrategy`](@ref) that uses a simple adaptive algorithm to compute the next time step

```
     dt = clamp(dx/vmax, dtmin, dtmax)
```
