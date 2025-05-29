```
inverse_retract(M::AbstractManifold, p, q)
inverse_retract(M::AbstractManifold, p, q, method::AbstractInverseRetractionMethod
```

Compute the inverse retraction, a cheaper, approximate version of the [`log`](@ref)arithmic map), of points `p` and `q` on the [`AbstractManifold`](@ref) `M`.

Inverse retraction method can be specified by the last argument, defaulting to [`default_inverse_retraction_method`](@ref)`(M)`. For available inverse retractions on certain manifolds see the documentation on the corresponding manifold.

See also [`retract`](@ref).
