```julia
∇(
    grid::SpeedyWeather.RingGrids.AbstractGridArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    kwargs...
) -> Tuple{Any, Any}

```

The zonal and meridional gradient of `grid`. Transform to spectral space, takes the gradient and unscales the 1/coslat scaling in the gradient. Acts on the unit-sphere, i.e. it omits 1/radius scaling unless `radius` keyword argument is provided. Makes use of an existing spectral transform `S`.
