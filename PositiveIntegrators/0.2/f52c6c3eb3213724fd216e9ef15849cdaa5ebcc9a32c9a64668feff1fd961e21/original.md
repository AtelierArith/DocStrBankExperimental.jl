```
SSPMPRK22(α, β; [linsolve = ..., small_constant = ...])
```

A family of second-order modified Patankar-Runge-Kutta algorithms for production-destruction systems. Each member of this family is an adaptive, one-step, two-stage method which is second-order accurate, unconditionally positivity-preserving, and linearly implicit. The parameters `α` and `β` are described by Huang and Shu (2019) and studied by Huang, Izgin, Kopecz, Meister and Shu (2023). The difference to [`MPRK22`](@ref) is that this method is based on the SSP formulation of an explicit second-order Runge-Kutta method. This family of schemes contains the [`MPRK22`](@ref) family, where `MPRK22(α) = SSMPRK22(0, α)` applies.

This method supports adaptive time stepping, using the first order approximations $(σ_i - u_i^n) / τ + u_i^n$ with $τ=1+(α_{21}β_{10}^2)/(β_{20}+β_{21})$, see (2.7) in Huang and Shu (2019), to estimate the error.

The scheme was introduced by Huang and Shu for conservative production-destruction systems. For nonconservative production–destruction systems we use the straight forward extension analogous to [`MPE`](@ref).

This modified Patankar-Runge-Kutta method requires the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. You can pass a value explicitly, otherwise `small_constant` is set to `floatmin` of the floating point type used.

## References

  * Juntao Huang and Chi-Wang Shu. "Positivity-Preserving Time Discretizations for Production–Destruction Equations with Applications to Non-equilibrium Flows." Journal of Scientific Computing 78 (2019): 1811–1839 [DOI: 10.1007/s10915-018-0852-1](https://doi.org/10.1007/s10915-018-0852-1)
  * Juntao Huang, Thomas Izgin, Stefan Kopecz, Andreas Meister and Chi-Wang Shu. "On the stability of strong-stability-preserving modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 57 (2023):1063–1086 [DOI: 10.1051/m2an/2023005](https://doi.org/10.1051/m2an/2023005)
