```
AbstractLieGroupPoint <: ManifoldsBase.AbstractManifoldPoint end
```

An abstract type for a point on an [`AbstractLieGroup`](@ref). While an points and tangent vectors are usually kept untyped for flexibility, it might be necessary to distinguish different types of points, for example

  * for complicated representations that require a struct
  * semantic verification
  * when there exist different representations

By sub-typing the [`AbstractManifoldPoint`](@extref `ManifoldsBase.AbstractManifoldPoint`), this follows the same idea as in [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/).
