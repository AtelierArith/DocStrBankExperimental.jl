```
GaussNewton(;
    concrete_jac = nothing, linsolve = nothing, linesearch = missing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

An advanced GaussNewton implementation with support for efficient handling of sparse matrices via colored automatic differentiation and preconditioned linear solvers. Designed for large-scale and numerically-difficult nonlinear systems.
