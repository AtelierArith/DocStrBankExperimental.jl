```julia
spectral_truncation!(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    ltrunc::Integer,
    mtrunc::Integer
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

Triangular truncation to degree `ltrunc` and order `mtrunc` (both 0-based). Truncate spectral coefficients `alms` in-place by setting all coefficients for which the degree `l` is larger than the truncation `ltrunc` or order `m` larger than the truncaction `mtrunc`.
