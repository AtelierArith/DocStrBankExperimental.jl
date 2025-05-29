```julia
∇(
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Tuple{Any, Any}

```

The zonal and meridional gradient of `p`. Precomputes a `SpectralTransform` `S`. Acts on the unit-sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided.
