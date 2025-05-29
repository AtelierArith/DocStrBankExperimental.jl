```julia
∇²(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Any

```

Laplace operator ∇² applied to input `alms`, using precomputed eigenvalues from `S`. Acts on the unit sphere, i.e. it omits 1/radius^2 scaling unless `radius` keyword argument is provided.
