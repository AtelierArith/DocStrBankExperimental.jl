```
outflows(sys)
```

Get the vector of outflow connectors of the system represented by the process element `sys`.

This function returns the outflows of the system. Outflows are all flows leaving the system.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which could have one or more outflows.
