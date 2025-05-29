```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GeodesicInterpolation;
    shuffle_rng=nothing,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x)),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x)),
    kwargs...,
)
```

Estimate the Riemannian center of mass of `x` in an online fashion using repeated weighted geodesic interpolation. See [`GeodesicInterpolation`](@extref `ManifoldsBase.GeodesicInterpolation`) for details.

If `shuffle_rng` is provided, it is used to shuffle the order in which the points are considered for computing the mean.

Optionally, pass `retraction` and `inverse_retraction` method types to specify the (inverse) retraction.
