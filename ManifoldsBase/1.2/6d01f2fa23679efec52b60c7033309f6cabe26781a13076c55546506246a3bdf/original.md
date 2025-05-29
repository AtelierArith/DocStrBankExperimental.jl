```
inverse_retract!(M::AbstractManifold, X, p, q[, method::AbstractInverseRetractionMethod])
```

Compute the inverse retraction, a cheaper, approximate version of the [`log`](@ref)arithmic map), of points `p` and `q` on the [`AbstractManifold`](@ref) `M`. Result is saved to `X`.

Inverse retraction method can be specified by the last argument, defaulting to [`default_inverse_retraction_method`](@ref)`(M)`. See the documentation of respective manifolds for available methods.

See also [`retract!`](@ref).
