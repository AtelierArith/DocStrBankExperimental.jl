```
vector_transport_to(M::AbstractPowerManifold, p, X, q, method::AbstractVectorTransportMethod)
```

Compute the vector transport the tangent vector `X`at `p` to `q` on the [`PowerManifold`](@ref) `M` using an [`AbstractVectorTransportMethod`](@ref) `m`. This method is performed elementwise, i.e. the method `m` has to be implemented on the base manifold.
