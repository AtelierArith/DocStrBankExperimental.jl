```
sfccsolve(obj::AbstractSFCCObjective, solver::SFCCSolver, x₀, ::Val{return_all}=Val{true}()) where {return_all}
```

Solve the given objective `obj` using `solver` and initial guess `x₀`. If `return_all=true`, then `sfccsolve` should return a named tuple with at least the temperature solution `T`, the liquid water content `θw`, the heat capacity `C`, and the liquid water content deriviative `∂θw∂T` defined. Solver-specific additional values may also be included.
