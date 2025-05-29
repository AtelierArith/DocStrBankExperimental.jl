```
vector_transport_direction(M::AbstractManifold, p, X, d)
vector_transport_direction(M::AbstractManifold, p, X, d, m::AbstractVectorTransportMethod)
```

Given an [`AbstractManifold`](@ref) $\mathcal M$ the vector transport is a generalization of the [`parallel_transport_direction`](@ref) that identifies vectors from different tangent spaces.

More precisely using [AbsilMahonySepulchre:2008](@cite), Def. 8.1.1, a vector transport $T_{p,d}: T_p\mathcal M \to T_q\mathcal M$, $p∈ \mathcal M$, $Y∈ T_p\mathcal M$ is a smooth mapping associated to a retraction $\operatorname{retr}_p(Y) = q$ such that

1. (associated retraction) $\mathcal T_{p,d}X ∈ T_q\mathcal M$ if and only if $q = \operatorname{retr}_p(d)$.
2. (consistency) $\mathcal T_{p,0_p}X = X$ for all $X∈T_p\mathcal M$
3. (linearity) $\mathcal T_{p,d}(αX+βY) = α\mathcal T_{p,d}X + β\mathcal T_{p,d}Y$

For the [`AbstractVectorTransportMethod`](@ref) we might even omit the third point. The [`AbstractLinearVectorTransportMethod`](@ref)s are linear.

# Input Parameters

  * `M` a manifold
  * `p` indicating the tangent space of
  * `X` the tangent vector to be transported
  * `d` indicating a transport direction (and distance through its length)
  * `m` an [`AbstractVectorTransportMethod`](@ref), by default [`default_vector_transport_method`](@ref), so usually [`ParallelTransport`](@ref)

Usually this method requires a [`AbstractRetractionMethod`](@ref) as well. By default this is assumed to be the [`default_retraction_method`](@ref) or implicitly given (and documented) for a vector transport. To explicitly distinguish different retractions for a vector transport, see [`VectorTransportDirection`](@ref).

Instead of spcifying a start direction `d` one can equivalently also specify a target tanget space $T_q\mathcal M$, see [`vector_transport_to`](@ref). By default [`vector_transport_direction`](@ref) falls back to using [`vector_transport_to`](@ref), using the [`default_retraction_method`](@ref) on `M`.
