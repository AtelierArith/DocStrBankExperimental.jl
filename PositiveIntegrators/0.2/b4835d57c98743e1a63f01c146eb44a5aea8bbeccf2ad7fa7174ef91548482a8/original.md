```
MPRK43I(α, β; [linsolve = ..., small_constant = ...])
```

A family of third-order modified Patankar-Runge-Kutta schemes for production-destruction systems, which is based on the two-parameter family of third order explicit Runge–Kutta schemes. Each member of this family is an adaptive, one-step method with four-stages which is third-order accurate, unconditionally positivity-preserving, conservative and linearly implicit. In this implementation the stage-values are conservative as well. The parameters `α` and `β` must be chosen such that the Runge–Kutta coefficients are nonnegative, see Kopecz and Meister (2018) for details.

These methods support adaptive time stepping, using the Patankar-weight denominators $σ_i$, see Kopecz and Meister (2018), as second order approximations to estimate the error.

The scheme was introduced by Kopecz and Meister for conservative production-destruction systems. For nonconservative production–destruction systems we use the straight forward extension analogous to [`MPE`](@ref).

These modified Patankar-Runge-Kutta methods require the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. You can pass a value explicitly, otherwise `small_constant` is set to `floatmin` of the floating point type used.

## References

  * Stefan Kopecz and Andreas Meister. "Unconditionally positive and conservative third order modified Patankar–Runge–Kutta  discretizations of production–destruction systems."  BIT Numerical Mathematics 58 (2018): 691–728. [DOI: 10.1007/s10543-018-0705-1](https://doi.org/10.1007/s10543-018-0705-1)
