```
vector_transport_direction!(M::AbstractManifold, Y, p, X, d)
vector_transport_direction!(M::AbstractManifold, Y, p, X, d, m::AbstractVectorTransportMethod)
```

Transport a vector `X` from the tangent space at a point `p` on the [`AbstractManifold`](@ref) `M` in the direction indicated by the tangent vector `d` at `p`. By default, [`retract`](@ref) and [`vector_transport_to!`](@ref) are used with the `m` and `r`, which default to [`default_vector_transport_method`](@ref)`(M)` and [`default_retraction_method`](@ref)`(M)`, respectively. The result is saved to `Y`.

See [`vector_transport_direction`](@ref) for more details.
