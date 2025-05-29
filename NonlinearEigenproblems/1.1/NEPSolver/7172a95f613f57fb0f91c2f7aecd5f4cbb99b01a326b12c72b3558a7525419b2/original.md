```
struct DefaultInnerSolver <: InnerSolver
```

Dispatches a version of [`inner_solve`](@ref) based on the type of the NEP provided. This function tries to automatically detect which solver is recommended.

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)
