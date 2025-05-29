```julia
curl!(
    curl::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    flipsign,
    add,
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Curl of a vector `u, v` written into `curl`, `curl = ∇×(u, v)`. `u, v` are expected to have a 1/coslat-scaling included, otherwise `curl` is scaled. Acts on the unit sphere, i.e. it omits 1/radius scaling as all gradient operators unless the `radius` keyword argument is provided. `flipsign` option calculates -∇×(u, v) instead. `add` option calculates `curl += ∇×(u, v)` instead. `flipsign` and `add` can be combined. This functions only creates the kernel and calls the generic divergence function _divergence! subsequently with flipped u, v -> v, u for the curl.
