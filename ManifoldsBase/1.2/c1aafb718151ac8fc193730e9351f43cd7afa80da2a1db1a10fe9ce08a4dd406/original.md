```
vector_transport_to!(M::AbstractManifold, Y, p, X, q)
vector_transport_to!(M::AbstractManifold, Y, p, X, q, m::AbstractVectorTransportMethod)
```

Transport a vector `X` from the tangent space at a point `p` on the [`AbstractManifold`](@ref) `M` to `q` using the [`AbstractVectorTransportMethod`](@ref) `m` and the [`AbstractRetractionMethod`](@ref) `r`.

The result is computed in `Y`. See [`vector_transport_to`](@ref) for more details.
