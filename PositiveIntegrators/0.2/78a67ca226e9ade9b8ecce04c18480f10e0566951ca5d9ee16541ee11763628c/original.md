```
SSPMPRK43([linsolve = ..., small_constant = ...])
```

A third-order modified Patankar-Runge-Kutta algorithm for production-destruction systems. This scheme is a one-step, four-stage method which is third-order accurate, unconditionally positivity-preserving, and linearly implicit. The scheme is described by Huang, Zhao and Shu (2019) and studied by Huang, Izgin, Kopecz, Meister and Shu (2023). The difference to [`MPRK43I`](@ref) or [`MPRK43II`](@ref) is that this method is based on the SSP formulation of an explicit third-order Runge-Kutta method.

The scheme was introduced by Huang, Zhao and Shu for conservative production-destruction systems. For nonconservative production–destruction systems we use the straight forward extension analogous to [`MPE`](@ref).

This modified Patankar-Runge-Kutta method requires the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. To display the default value for data type `type` evaluate `SSPMPRK43. small_constant_function(type)`, where `type` can be, e.g., `Float64`.

The current implementation only supports fixed time steps.

## References

  * Juntao Huang, Weifeng Zhao and Chi-Wang Shu. "A Third-Order Unconditionally Positivity-Preserving Scheme for Production–Destruction Equations with Applications to Non-equilibrium Flows." Journal of Scientific Computing 79 (2019): 1015–1056 [DOI: 10.1007/s10915-018-0881-9](https://doi.org/10.1007/s10915-018-0881-9)
  * Juntao Huang, Thomas Izgin, Stefan Kopecz, Andreas Meister and Chi-Wang Shu. "On the stability of strong-stability-preserving modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 57 (2023):1063–1086 [DOI: 10.1051/m2an/2023005](https://doi.org/10.1051/m2an/2023005)
