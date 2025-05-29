```
vector_transport_to(M::AbstractManifold, p, X, q)
vector_transport_to(M::AbstractManifold, p, X, q, m::AbstractVectorTransportMethod)
vector_transport_to(M::AbstractManifold, p, X, q, m::AbstractVectorTransportMethod)
```

Transport a vector `X` from the tangent space at a point `p` on the [`AbstractManifold`](@ref) `M` along a curve implicitly given by an [`AbstractRetractionMethod`](@ref) associated to `m`. By default `m` is the [`default_vector_transport_method`](@ref)`(M)`. To explicitly specify a (different) retraction to the implicitly assumeed retraction, see [`VectorTransportTo`](@ref). Note that some vector transport methods might also carry their own retraction they are associated to, like the  [`DifferentiatedRetractionVectorTransport`](@ref) and some are even independent of the retraction, for example the [`ProjectionTransport`](@ref).

This method is equivalent to using $d = \operatorname{retr}^{-1}_p(q)$ in [`vector_transport_direction`](@ref)`(M, p, X, q, m, r)`, where you can find the formal definition. This is the fallback for [`VectorTransportTo`](@ref).
