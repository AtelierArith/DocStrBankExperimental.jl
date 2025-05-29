```
vector_transport_to(M::ProductManifold, p, X, q, m::AbstractVectorTransportMethod)
```

Compute the vector transport the tangent vector `X` at `p` to `q` on the [`ProductManifold`](@ref) `M` using an [`AbstractVectorTransportMethod`](@ref) `m` on each manifold.
