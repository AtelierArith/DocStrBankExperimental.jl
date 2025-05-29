```
extract_point_states(system, assembly; prescribed_conditions = Dict())
extract_point_states(x, system, assembly; prescribed_conditions = Dict())
extract_point_states(dx, x, system, assembly; prescribed_conditions = Dict())
```

Return the state variables corresponding to each point (see [`PointState`](@ref)) given the state vector `x` and rate vector `dx`.

If `prescribed_conditions` is not provided, all point state variables are assumed to be displacements/rotations, rather than their actual identities as used in the analysis.
