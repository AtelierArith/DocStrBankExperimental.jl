```
Subsystem{T, Eltype, StateNT, ParamNT}
```

A `Subsystem` struct describes a complete subcomponent to an `GraphSystem`. This stores a `SubsystemStates` to describe the continuous dynamical state of the subsystem, and a `GraphSystemParams` which describes various non-dynamical parameters of the subsystem. The type parameter `T` is the subsystem's "tag" which labels what sort of subsystem it is.

See also `subsystem_differential`, `SubsystemStates`, `SubsystemParams`.

For example, if we wanted to describe a system where one sub-component is a billiard ball,
