```julia
spectral_truncation!(
    A::AbstractMatrix
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{T, 2, ArrayType} where {T, ArrayType<:AbstractMatrix{T}}

```

`A`の上三角をゼロに設定します。
