```
ode_norm(u, t)
```

Implementation of the weighted L2 norm of Hairer and Wanner used for error-based step size control in OrdinaryDiffEq.jl. This function is aware of MPI and uses global MPI communication when running in parallel.

You must pass this function as a keyword argument `internalnorm = ode_norm` to OrdinaryDiffEq.jl's `solve` when using error-based step size control with MPI parallel execution of Trixi.jl.

See the "Advanced Adaptive Stepsize Control" section of the [documentation](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/).
