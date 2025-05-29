```julia
transform(
    specs::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    unscale_coslat,
    kwargs...
) -> Any

```

Spectral transform (spectral to grid space) from spherical coefficients `alms` to a newly allocated gridded field `map`. Based on the size of `alms` the grid type `grid`, the spatial resolution is retrieved based on the truncation defined for `grid`. SpectralTransform struct `S` is allocated to execute `transform(alms, S)`.
