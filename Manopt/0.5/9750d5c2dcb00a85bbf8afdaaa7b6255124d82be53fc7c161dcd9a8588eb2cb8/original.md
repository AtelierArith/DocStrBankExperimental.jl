```
ManifoldCostObjective{T, TC} <: AbstractManifoldCostObjective{T, TC}
```

specify an [`AbstractManifoldObjective`](@ref) that does only have information about the cost function $f:  \mathbb M → ℝ$ implemented as a function `(M, p) -> c` to compute the cost value `c` at `p` on the manifold `M`.

  * `cost`: a function $f: \mathcal M → ℝ$ to minimize

# Constructors

```
ManifoldCostObjective(f)
```

Generate a problem. While this Problem does not have any allocating functions, the type `T` can be set for consistency reasons with other problems.

# Used with

[`NelderMead`](@ref), [`particle_swarm`](@ref)
