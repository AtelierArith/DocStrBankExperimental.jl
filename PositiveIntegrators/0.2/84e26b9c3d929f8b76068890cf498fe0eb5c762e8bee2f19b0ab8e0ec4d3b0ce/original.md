```
MPDeC(K; [nodes = :gausslobatto, linsolve = ..., small_constant = ...])
```

A family of arbitrary order modified Patankar-Runge-Kutta algorithms for production-destruction systems. Each member of this family is an adaptive, one-step method which is Kth order accurate, unconditionally positivity-preserving, and linearly implicit. The integer K must be chosen to satisfy 2 ≤ K ≤ 10. Available node choices are Lagrange or Gauss-Lobatto nodes, with the latter being the default. These methods support adaptive time stepping, using the numerical solution obtained with one correction step less as a lower-order approximation to estimate the error. The MPDeC schemes were introduced by Torlo and Öffner (2020) for autonomous conservative production-destruction systems and further investigated in Torlo, Öffner and Ranocha (2022).

For nonconservative production–destruction systems we use a straight forward extension analogous to [`MPE`](@ref). A general discussion of DeC schemes applied to non-autonomous differential equations and using general integration nodes is given by Ong and Spiteri (2020).

The MPDeC methods require the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. You can pass a value explicitly, otherwise `small_constant` is set to `1e-300` in double precision computations or `floatmin` of the floating point type used.

## References

  * Davide Torlo and Philipp Öffner. "Arbitrary high-order, conservative and positivity preserving Patankar-type deferred correction schemes." Applied Numerical Mathematics 153 (2020): 15-34. [DOI: 10.1016/j.apnum.2020.01.025](https://doi.org/10.1016/j.apnum.2020.01.025)
  * Davide Torlo, Philipp Öffner, and Hendrik Ranocha. "Issues with positivity-preserving Patankar-type schemes." Applied Numerical Mathematics 182 (2022): 117-147. [DOI: 10.1016/j.apnum.2022.07.014](https://doi.org/10.1016/j.apnum.2022.07.014)
  * Benjamin W. Ong and Raymond J. Spiteri. "Deferred Correction Methods for Ordinary Differential Equations." Journal of Scientific Computing 83 (2020): Article 60. [DOI: 10.1007/s10915-020-01235-8](https://doi.org/10.1007/s10915-020-01235-8)
