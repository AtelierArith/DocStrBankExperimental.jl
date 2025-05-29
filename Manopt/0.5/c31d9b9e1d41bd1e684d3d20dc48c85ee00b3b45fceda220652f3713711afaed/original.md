```
LiuStoreyCoefficient(; kwargs...)
LiuStoreyCoefficient(M::AbstractManifold; kwargs...)
```

Computes an update coefficient for the [`conjugate_gradient_descent`](@ref) algorithm based on [LiuStorey:1991](@cite) adapted to manifolds

Denote the last iterate and gradient by $p_k,X_k$, the current iterate and gradient by $p_{k+1}, X_{k+1}$, respectively, as well as the last update direction by $δ_k$.

Let $ν_k = X_{k+1} - \mathcal T_{p_{k+1}←p_k}X_k$, where $\mathcal T_{⋅←⋅}$ denotes a vector transport.

Then the coefficient reads

$$
β_k = - \frac{⟨ X_{k+1},ν_k ⟩_{p_{k+1}}}{⟨ δ_k,X_k ⟩_{p_k}}.
$$

# Keyword arguments

  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a vector transport $\mathcal T_{⋅←⋅}$ to use, see [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

!!! info
    This function generates a [`ManifoldDefaultsFactory`](@ref) for [`LiuStoreyCoefficientRule`](@ref). For default values, that depend on the manifold, this factory postpones the construction until the manifold from for example a corresponding [`AbstractManoptSolverState`](@ref) is available.

