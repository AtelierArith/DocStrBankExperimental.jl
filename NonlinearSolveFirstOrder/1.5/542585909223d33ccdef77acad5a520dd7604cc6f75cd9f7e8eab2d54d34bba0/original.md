```
PseudoTransient(;
    concrete_jac = nothing, linesearch = missing, alpha_initial = 1e-3,
    linsolve = nothing,
    autodiff = nothing, jvp_autodiff = nothing, vjp_autodiff = nothing
)
```

An implementation of PseudoTransient Method [coffey2003pseudotransient](@cite) that is used to solve steady state problems in an accelerated manner. It uses an adaptive time-stepping to integrate an initial value of nonlinear problem until sufficient accuracy in the desired steady-state is achieved to switch over to Newton's method and gain a rapid convergence. This implementation specifically uses "switched evolution relaxation" [kelley1998convergence](@cite) SER method.

### Keyword Arguments

  * `alpha_initial` : the initial pseudo time step. It defaults to `1e-3`. If it is small, you are going to need more iterations to converge but it can be more stable.
