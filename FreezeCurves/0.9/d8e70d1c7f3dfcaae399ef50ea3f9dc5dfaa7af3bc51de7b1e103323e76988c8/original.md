```
sfccsolve(obj::SFCCInverseEnthalpyObjective, solver::SFCCNewtonSolver, T₀::Number, ::Val{return_all}=Val{true}(); error_when_not_converged=true)
```

Solves `obj` using the specialized Newton `solver` and returns the result. If `return_all` is `true`, a named tuple `(;T, Tres, θw, C, itercount)` is returned; otherwise (by default), only the temperature solution is returned.
