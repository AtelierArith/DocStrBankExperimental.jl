```
AssemblyState(system, assembly; prescribed_conditions = Dict())
AssemblyState(x, system, assembly; prescribed_conditions = Dict())
AssemblyState(dx, x, system, assembly; prescribed_conditions = Dict())
```

Post-process the system state given the state vector `x` and rate vector `dx`.  Return an object of type `AssemblyState` that defines the state of the assembly for the time step.

If `prescribed_conditions` is not provided, all point state variables are assumed to be displacements/rotations, rather than their actual identities as used in the analysis.
