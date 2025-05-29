```
AutoAlgorithm{T, M <: Manifold}(manifold::M, x::T)
```

Indicates that the [`Operation`](@ref) should automatically select the best algorithm for its input data, based on the passed in manifold (may be an [`AutoManifold`](@ref)) and data  `x`.

The actual implementation is left to the implementation of that particular [`Operation`](@ref).
