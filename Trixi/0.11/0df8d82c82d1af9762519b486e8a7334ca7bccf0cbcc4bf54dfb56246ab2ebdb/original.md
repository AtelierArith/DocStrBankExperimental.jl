```
ode_unstable_check(dt, u, semi, t)
```

Implementation of the basic check for instability used in OrdinaryDiffEq.jl. Instead of checking something like `any(isnan, u)`, this function just checks `isnan(dt)`. This helps when using MPI parallelization, since no additional global communication is required and all ranks will return the same result.

You should pass this function as a keyword argument `unstable_check=ode_unstable_check` to OrdinaryDiffEq.jl's  `solve` when using error-based step size control with MPI parallel execution of Trixi.jl.

See the "Miscellaneous" section of the [documentation](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/).
