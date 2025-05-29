```
fit!(mach::Machine, rows=nothing, verbosity=1, force=false, composite=nothing)
```

Fit the machine `mach`. In the case that `mach` has `Node` arguments, first train all other machines on which `mach` depends.

To attempt to fit a machine without touching any other machine, use `fit_only!`. For more on options and the the internal logic of fitting see [`fit_only!`](@ref)
