Automatic switching algorithm that can switch between the (non-stiff) `Vern7()` and `stiff_alg`.

```
AutoVern7(stiff_alg; kwargs...)
```

This method is equivalent to `AutoAlgSwitch(Vern7(), stiff_alg; kwargs...)`. To gain access to stiff algorithms you might have to install additional libraries, such as `OrdinaryDiffEqRosenbrock`.
