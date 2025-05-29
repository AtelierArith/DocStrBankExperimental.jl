```
ode_default_options()
```

Return the default options for OrdinaryDiffEq's `solve`. Pass `ode_default_options()...` to `solve` to only return the solution at the final time and enable **MPI aware** error-based step size control, whenever MPI is used. For example, use `solve(ode, alg; ode_default_options()...)`.
