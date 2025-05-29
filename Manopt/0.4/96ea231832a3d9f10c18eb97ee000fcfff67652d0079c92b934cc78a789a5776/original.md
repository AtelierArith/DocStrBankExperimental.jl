```
ManifoldSubgradientObjective{T<:AbstractEvaluationType,C,S} <:AbstractManifoldCostObjective{T, C}
```

A structure to store information about a objective for a subgradient based optimization problem

# Fields

  * `cost`:        the function $f$ to be minimized
  * `subgradient`: a function returning a subgradient $∂f$ of $f$

# Constructor

```
ManifoldSubgradientObjective(f, ∂f)
```

Generate the [`ManifoldSubgradientObjective`](@ref) for a subgradient objective, consisting of a (cost) function `f(M, p)` and a function `∂f(M, p)` that returns a not necessarily deterministic element from the subdifferential at `p` on a manifold `M`.
