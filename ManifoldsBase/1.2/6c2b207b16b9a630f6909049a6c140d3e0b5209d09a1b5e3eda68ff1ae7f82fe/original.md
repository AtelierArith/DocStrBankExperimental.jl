```
ValidationMPoint{P} <: AbstractManifoldPoint
```

Represent a point on an [`ValidationManifold`](@ref). The point is stored internally.

# Fields

  * `value::P`: the internally stored point on a manifold

# Constructor

```
    ValidationMPoint(value)
```

Create a point on the manifold with the value `value`.
