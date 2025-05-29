```
AbstractHessianSolverState <: AbstractGradientSolverState
```

An [`AbstractManoptSolverState`](@ref) type to represent algorithms that employ the Hessian. These options are assumed to have a field (`gradient`) to store the current gradient $\operatorname{grad}f(x)$
