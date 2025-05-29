```julia
divergence!(
    div::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    flipsign,
    add,
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Divergence of a vector `u, v` written into `div`, `div = ∇⋅(u, v)`.  `u, v` are expected to have a 1/coslat-scaling included, otherwise `div` is scaled. Acts on the unit sphere, i.e. it omits 1/radius scaling as all gradient operators, unless the `radius` keyword argument is provided. `flipsign` option calculates -∇⋅(u, v) instead. `add` option calculates `div += ∇⋅(u, v)` instead. `flipsign` and `add` can be combined. This functions only creates the kernel and calls the generic divergence function _divergence! subsequently.
