```julia
spectral_truncation(
    _::Type{NF},
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{T, N, ArrayType},
    ltrunc::Integer,
    mtrunc::Integer
) -> Any

```

Returns a LowerTriangularArray that is truncated from `alms` to the size (`ltrunc`+1) x (`mtrunc`+1), both inputs are 0-based. If `ltrunc` or `mtrunc` is larger than the corresponding size of`alms` than `spectral_interpolation` is automatically called instead, returning a LowerTriangularArray padded zero coefficients for higher wavenumbers.
