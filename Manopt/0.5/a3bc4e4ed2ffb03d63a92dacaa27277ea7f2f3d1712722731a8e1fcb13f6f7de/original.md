```
 SimpleManifoldCachedObjective{O<:AbstractManifoldGradientObjective{E,TC,TG}, P, T,C} <: AbstractManifoldGradientObjective{E,TC,TG}
```

Provide a simple cache for an [`AbstractManifoldGradientObjective`](@ref) that is for a given point `p` this cache stores a point `p` and a gradient $\operatorname{grad} f(p)$ in `X` as well as a cost value $f(p)$ in `c`.

Both `X` and `c` are accompanied by booleans to keep track of their validity.

# Constructor

```
SimpleManifoldCachedObjective(M::AbstractManifold, obj::AbstractManifoldGradientObjective; kwargs...)
```

## Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold to initialize the cache with
  * `X=get_gradient(M, obj, p)` or `zero_vector(M,p)`: a tangent vector to store the gradient in, see also `initialize=`
  * `c=[`get_cost`](@ref)`(M, obj, p)`or`0.0`: a value to store the cost function in`initialize`
  * `initialized=true`: whether to initialize the cached `X` and `c` or not.
