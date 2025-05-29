A package providing a common interface to integration algorithms intended for applications including Brillouin-zone integration and Wannier interpolation. Its design is influenced by high-level libraries like Integrals.jl to implement the CommonSolve.jl interface, and it makes use of Julia's multiple dispatch to provide the same interface for integrands with optimized inplace, batched, and Fourier series evaluation.

### Quickstart

As a first example, we integrate sine over [0,1] as a function of its period.

```
julia> using AutoBZCore

julia> prob = IntegralProblem((x,p) -> sin(p*x), (0, 1), 0.3);

julia> solve(prob, QuadGKJL()).value # solves the integral of sin(p*x) over [0,1] with p=0.3
0.14887836958131329
```

Notice that we construct an [`IntegralProblem`](@ref) object that we can [`solve`](@ref) at with a choice of algorithm. For more examples, see the documentation.

### Features

Special integrand interfaces

  * [`IntegralFunction`](@ref): generic user integrand of the form `f(x, p)`
  * [`InplaceIntegralFunction`](@ref): allows an integrand to write its result inplace to an array
  * [`InplaceBatchIntegralFunction`](@ref): allows user-side parallelization on e.g. shared memory, distributed memory, or the gpu
  * [`CommonSolveIntegralFunction`](@ref): define an integrand that also solves a problem
  * [`FourierIntegralFunction`](@ref): efficient evaluation of Fourier series for cubatures with hierachical grids

Quadrature algorithms:

  * Trapezoidal rule and FastGaussQuadrature.jl: [`QuadratureFunction`](@ref)
  * h-adaptive quadrature (Gauss-Kronrod): [`QuadGKJL`](@ref)
  * h-adaptive cubature (Genz-Malik): [`HCubatureJL`](@ref)
  * p-adaptive, symmetrized Monkhorst-Pack: [`AutoSymPTRJL`](@ref)

Meta-Algorithms:

  * Iterated integration: [`NestedQuad`](@ref)

# Extended help

If you experience issues with AutoBZCore.jl, please report a bug on the [GitHub page](https://github.com/lxvm/AutoBZCore.jl) to contact the developers.
