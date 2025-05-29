```
MPRK22(α; [linsolve = ..., small_constant = ...])
```

A family of second-order modified Patankar-Runge-Kutta algorithms for production-destruction systems. Each member of this family is an adaptive, one-step, two-stage method which is second-order accurate, unconditionally positivity-preserving, and linearly implicit. In this implementation the stage-values are conservative as well. The parameter `α` is described by Kopecz and Meister (2018) and studied by Izgin, Kopecz and Meister (2022) as well as Torlo, Öffner and Ranocha (2022).

This method supports adaptive time stepping, using the Patankar-weight denominators $σ_i$, see Kopecz and Meister (2018), as first order approximations to estimate the error.

The scheme was introduced by Kopecz and Meister for conservative production-destruction systems. For nonconservative production–destruction systems we use a straight forward extension analogous to [`MPE`](@ref).

This modified Patankar-Runge-Kutta method requires the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. You can pass a value explicitly, otherwise `small_constant` is set to `floatmin` of the floating point type used.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
  * Stefan Kopecz and Andreas Meister. "On order conditions for modified Patankar-Runge-Kutta schemes." Applied Numerical Mathematics 123 (2018): 159-179. [DOI: 10.1016/j.apnum.2017.09.004](https://doi.org/10.1016/j.apnum.2017.09.004)
  * Thomas Izgin, Stefan Kopecz, and Andreas Meister. "On Lyapunov stability of positive and conservative time integrators and application to second order modified Patankar-Runge-Kutta schemes." ESAIM: Mathematical Modelling and Numerical Analysis 56.3 (2022): 1053-1080. [DOI: 10.1051/m2an/2022031](https://doi.org/10.1051/m2an/2022031)
  * Davide Torlo, Philipp Öffner, and Hendrik Ranocha. "Issues with positivity-preserving Patankar-type schemes." Applied Numerical Mathematics 182 (2022): 117-147. [DOI: 10.1016/j.apnum.2022.07.014](https://doi.org/10.1016/j.apnum.2022.07.014)
