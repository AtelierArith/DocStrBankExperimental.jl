```
extract_element_states(system, assembly, x = system.x, dx = system.dx;
    prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}())
```

Return the state variables corresponding to each element (see [`ElementState`](@ref)) given the solution vector `x`.
