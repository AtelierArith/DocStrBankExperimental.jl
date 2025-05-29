```julia
∇⁻²(
    ∇²alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Any

```

InverseLaplace operator ∇⁻² applied to input `alms`, using precomputed eigenvalues from `S`. Acts on the unit sphere, i.e. it omits radius^2 scaling unless `radius` keyword argument is provided.
