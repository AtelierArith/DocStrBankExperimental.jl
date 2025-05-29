```julia
spectral_truncation!(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    trunc::Integer
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Triangular truncation of `alms` to degree and order `trunc` in-place.
