```julia
spectral_truncation!(
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    trunc::Integer
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

`alms`の三角トランケーションを次数と順序`trunc`に対してインプレースで行います。
