```
AbstractManoptProblem{M<:AbstractManifold}
```

Describe a Riemannian optimization problem with all static (not-changing) properties.

The most prominent features that should always be stated here are

  * the [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$
  * the cost function $f:  \mathcal M → ℝ$

Usually the cost should be within an [`AbstractManifoldObjective`](@ref).
