Automatic switching algorithm that can switch between the (non-stiff) `Vern8()` and `stiff_alg`.

```
AutoVern8(stiff_alg; kwargs...)
```

This method is equivalent to `AutoAlgSwitch(Vern8(), stiff_alg; kwargs...)`. To gain access to stiff algorithms you might have to install additional libraries, such as `OrdinaryDiffEqRosenbrock`.
