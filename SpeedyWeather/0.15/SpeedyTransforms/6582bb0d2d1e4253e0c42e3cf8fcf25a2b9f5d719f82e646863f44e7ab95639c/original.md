```julia
∇!(
    dpdx::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    dpdy::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    p::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    S::SpeedyWeather.SpeedyTransforms.SpectralTransform;
    radius
) -> Tuple{SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray, SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray}

```

Applies the gradient operator ∇ applied to input `p` and stores the result in `dpdx` (zonal derivative) and `dpdy` (meridional derivative). The gradient operator acts on the unit sphere and therefore omits the 1/radius scaling unless `radius` keyword argument is provided.
