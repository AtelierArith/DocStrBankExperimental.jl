```
inflows(sys)
```

Get the vector of inflow connectors of the system represented by the process element `sys`.

This function returns the inflows of the system. Inflows are all flows into the system.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which could have one or more inflows.
