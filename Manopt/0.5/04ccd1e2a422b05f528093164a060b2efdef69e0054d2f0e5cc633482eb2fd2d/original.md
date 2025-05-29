```
get_gradient(M::AbstractManifold, mgo::AbstractManifoldGradientObjective{T}, p)
get_gradient!(M::AbstractManifold, X, mgo::AbstractManifoldGradientObjective{T}, p)
```

evaluate the gradient of a [`AbstractManifoldGradientObjective{T}`](@ref) `mgo` at `p`.

The evaluation is done in place of `X` for the `!`-variant. The `T=`[`AllocatingEvaluation`](@ref) problem might still allocate memory within. When the non-mutating variant is called with a `T=`[`InplaceEvaluation`](@ref) memory for the result is allocated.

Note that the order of parameters follows the philosophy of `Manifolds.jl`, namely that even for the mutating variant, the manifold is the first parameter and the (in-place) tangent vector `X` comes second.
