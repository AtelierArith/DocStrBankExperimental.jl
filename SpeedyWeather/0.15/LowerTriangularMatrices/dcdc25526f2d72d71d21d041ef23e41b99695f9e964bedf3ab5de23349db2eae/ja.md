```julia
eachharmonic(
    L1::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    Ls::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray...
) -> Any

```

は、引数として提供されたLowerTriangularMatrices内のすべての非ゼロ要素をループするための`unit_range::UnitRange`を作成します。最初に境界をチェックします。すべてのLowerTriangularMatrixは同じサイズである必要があります。`eachindex`のようですが、`L`内のゼロの上三角をスキップします。
