```julia
∇(
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Tuple{Any, Any}

```

The zonal and meridional gradient of `p` using an existing `SpectralTransform` `S`. Acts on the unit sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided.
