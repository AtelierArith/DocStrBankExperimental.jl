```
prob = discretize(pde_system::PDESystem, discretization::PhysicsInformedNN)
```

Transforms a symbolic description of a ModelingToolkit-defined `PDESystem` and generates an `OptimizationProblem` for [Optimization.jl](https://docs.sciml.ai/Optimization/stable/) whose solution is the solution to the PDE.
