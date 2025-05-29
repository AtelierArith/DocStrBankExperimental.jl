```
AbstractManifoldPoint
```

Type for a point on a manifold. While an [`AbstractManifold`](@ref) does not necessarily require this type, for example when it is implemented for `Vector`s or `Matrix` type elements, this type can be used either

  * for more complicated representations,
  * semantic verification, or
  * when dispatching on different representations of points on a manifold.

Since semantic verification and different representations usually might still only store a matrix internally, it is possible to use [`@manifold_element_forwards`](@ref) and [`@default_manifold_fallbacks`](@ref) to reduce implementation overhead.
