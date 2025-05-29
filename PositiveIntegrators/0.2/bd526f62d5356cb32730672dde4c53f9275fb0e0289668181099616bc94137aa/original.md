```
MPE([linsolve = ..., small_constant = ...])
```

The first-order modified Patankar-Euler algorithm for production-destruction systems. This one-step, one-stage method is first-order accurate, unconditionally positivity-preserving, and linearly implicit.

The scheme was introduced by Burchard et al. for conservative production-destruction systems. For nonconservative production–destruction systems we use the straight forward extension

$u_i^{n+1} = u_i^n + Δt \sum_{j, j≠i} \biggl(p_{ij}^n \frac{u_j^{n+1}}{u_j^n}-d_{ij}^n \frac{u_i^{n+1}}{u_i^n}\biggr) + {\Delta}t p_{ii}^n - Δt d_{ii}^n\frac{u_i^{n+1}}{u_i^n}$,

where $p_{ij}^n = p_{ij}(t^n,\mathbf u^n)$ and $d_{ij}^n = d_{ij}(t^n,\mathbf u^n)$.

The modified Patankar-Euler method requires the special structure of a [`PDSProblem`](@ref) or a [`ConservativePDSProblem`](@ref).

You can optionally choose the linear solver to be used by passing an algorithm from [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl) as keyword argument `linsolve`. You can also choose the parameter `small_constant` which is added to all Patankar-weight denominators to avoid divisions by zero. You can pass a value explicitly, otherwise `small_constant` is set to `floatmin` of the floating point type used.

The current implementation only supports fixed time steps.

## References

  * Hans Burchard, Eric Deleersnijder, and Andreas Meister. "A high-order conservative Patankar-type discretisation for stiff systems of production-destruction equations." Applied Numerical Mathematics 47.1 (2003): 1-30. [DOI: 10.1016/S0168-9274(03)00101-6](https://doi.org/10.1016/S0168-9274(03)00101-6)
