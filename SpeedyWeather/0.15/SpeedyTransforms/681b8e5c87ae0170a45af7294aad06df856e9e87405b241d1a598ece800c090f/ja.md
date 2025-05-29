```julia
spectral_truncation(
    _::Type{NF},
    alms::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray{T, N, ArrayType},
    ltrunc::Integer,
    mtrunc::Integer
) -> Any

```

`alms`からサイズ（`ltrunc`+1）x（`mtrunc`+1）に切り詰められたLowerTriangularArrayを返します。両方の入力は0ベースです。`ltrunc`または`mtrunc`が`alms`の対応するサイズより大きい場合は、代わりに`spectral_interpolation`が自動的に呼び出され、高い波数のためにゼロ係数でパディングされたLowerTriangularArrayが返されます。
