```
AbstractManifoldGradientObjective{E<:AbstractEvaluationType, TC, TG} <: AbstractManifoldCostObjective{E, TC}
```

An abstract type for all objectives that provide a (full) gradient, where `T` is a [`AbstractEvaluationType`](@ref) for the gradient function.
