```julia
spectral_truncation!(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Triangular truncation of `alms` to the size of it, sets additional rows to zero.
