```
extract_point_state(system, assembly, ipoint; prescribed_conditions = Dict())
extract_point_state(x, system, assembly, ipoint; prescribed_conditions = Dict())
extract_point_state(dx, x, system, assembly, ipoint; prescribed_conditions = Dict())
```

Return the state variables corresponding to point `ipoint` (see [`PointState`](@ref)) given the state vector `x` and rate vector `dx`.

If `prescribed_conditions` is not provided, all point state variables are assumed to be displacements/rotations, rather than their actual identities as used in the analysis.
