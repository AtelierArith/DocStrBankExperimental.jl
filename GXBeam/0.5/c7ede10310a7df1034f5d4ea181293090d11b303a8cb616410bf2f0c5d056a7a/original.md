```
extract_element_state(system, assembly, ielem; prescribed_conditions = Dict())
extract_element_state(x, system, assembly, ielem; prescribed_conditions = Dict())
extract_element_state(dx, x, system, assembly, ielem; prescribed_conditions = Dict())
```

Return the state variables corresponding to element `ielem` (see [`ElementState`](@ref)) given the state vector `x` and rate vector `dx`.
