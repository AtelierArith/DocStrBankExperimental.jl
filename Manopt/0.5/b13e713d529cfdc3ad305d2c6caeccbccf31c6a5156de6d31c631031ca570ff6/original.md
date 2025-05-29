```
AverageGradient(; kwargs...)
AverageGradient(M::AbstractManifold; kwargs...)
```

Add an average of gradients to a gradient processor. A set of previous directions (from the inner processor) and the last iterate are stored, average is taken after vector transporting them to the current iterates tangent space.

# Input

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: a Riemannian manifold $\mathcal M$ (optional)

# Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$to specify the initial value
  * `direction=`[`IdentityUpdateRule`](@ref) preprocess the actual gradient before adding momentum
  * `gradients=[zero_vector(M, p) for _ in 1:n]` how to initialise the internal storage
  * `n=10` number of gradient evaluations to take the mean over
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`AverageGradientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

