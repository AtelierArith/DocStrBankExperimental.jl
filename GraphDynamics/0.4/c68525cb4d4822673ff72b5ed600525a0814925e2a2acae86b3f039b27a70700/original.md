```
 subsystem_differential(subsystem, input, t)
```

Add methods to this function to describe the derivatives of a given subsystem at time `t`. This should take in `Subsystem{T}` and return a `SubsystemStates{T}` where each element corresponds to the derivative of the subsystem with respect to that element. The `input` argument will be the total of all the `combine`'d inputs from all Subsystems which are connected to `subsystem` in the system graph.
