```julia
eachmatrix(
    L1::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    Ls::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray...
) -> Any

```

LowerTriangularArraysの非水平方向の次元に対するイテレータ。`lowertriangular_match`に従ってLowerTriangularArraysが一致することを確認します。
