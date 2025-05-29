```julia
struct PerturbedOracle{D, F, t, variance_reduction, G, R, S} <: InferOpt.AbstractOptimizationLayer
```

Differentiable perturbation of a black box optimizer of type `F`, with perturbation of type `D`.

This struct is as wrapper around `Reinforce` from DifferentiableExpectations.jl.

There are three different available constructors that behave differently in the package:

  * [`PerturbedOracle`](@ref)
  * [`PerturbedAdditive`](@ref)
  * [`PerturbedMultiplicative`](@ref)
