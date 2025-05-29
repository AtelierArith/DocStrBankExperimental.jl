```
MomentumGradient()
```

Append a momentum to a gradient processor, where the last direction and last iterate are stored and the new is composed as $η_i = m*η_{i-1}' - s d_i$, where $sd_i$ is the current (inner) direction and $η_{i-1}'$ is the vector transported last direction multiplied by momentum $m$.

# Input

  * `M` (optional)

# Keyword arguments

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: a point on the manifold $\mathcal M$
  * `direction=`[`IdentityUpdateRule`](@ref) preprocess the actual gradient before adding momentum
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: a tangent vector at the point $p$ on the manifold $\mathcal M$
  * `momentum=0.2` amount of momentum to use
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`MomentumGradientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

