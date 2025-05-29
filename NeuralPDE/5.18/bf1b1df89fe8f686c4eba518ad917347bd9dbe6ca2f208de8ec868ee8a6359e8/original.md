```
prob = symbolic_discretize(pde_system::PDESystem, discretization::AbstractPINN)
```

`symbolic_discretize` is the lower level interface to `discretize` for inspecting internals. It transforms a symbolic description of a ModelingToolkit-defined `PDESystem` into a `PINNRepresentation` which holds the pieces required to build an `OptimizationProblem` for [Optimization.jl](https://docs.sciml.ai/Optimization/stable) or a Likelihood Function used for HMC based Posterior Sampling Algorithms [AdvancedHMC.jl](https://turinglang.org/AdvancedHMC.jl/stable/) which is later optimized upon to give Solution or the Solution Distribution of the PDE.

For more information, see `discretize` and `PINNRepresentation`.
