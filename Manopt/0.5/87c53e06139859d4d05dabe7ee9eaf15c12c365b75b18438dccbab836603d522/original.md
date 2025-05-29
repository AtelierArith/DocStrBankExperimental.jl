```
StochasticGradient(; kwargs...)
StochasticGradient(M::AbstractManifold; kwargs...)
```

# Keyword arguments

  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`StochasticGradientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

